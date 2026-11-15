# HTTP API

VNote 4.14 introduced an optional **HTTP API** for local automation clients and agents. It runs inside the normal primary VNote application, not as a headless service or an MCP server. This guide targets VNote 4.14.4; the [upstream API guide](https://github.com/vnotex/vnote/blob/v4.14.4/docs/http-api.md) and [OpenAPI contract](https://github.com/vnotex/vnote/blob/v4.14.4/docs/http-api.openapi.yaml) describe the full protocol.

## Enable a client

1. Keep the notebooks you want to authorize open, then go to **Settings → HTTP API**.
2. Under **Client Tokens**, click **New**. Enter a label, select the notebooks and permissions, and choose an expiry in **Issue Client Token**. New grants default to **read-only** and **90 days**; expiry choices are 1, 7, 30, 60, 90, or 180 days, or **Never**. Notebooks opened or created later are not automatically added to a grant.
3. Choose **Issue Token**, then **Copy** while the token is displayed. The secret is shown **only once** and cannot be recovered from VNote. Store it in the client's secret store, not in a note, URL, command history, source control, or an agent's tool arguments. Closing the dialog does not clear the clipboard; clear it yourself after storing the token securely.
4. Enable the listener at **`127.0.0.1:18765`**, or select another explicit port. Explicit IPv6 loopback `::1` is also supported. Wildcard/public binds and automatic fallback to another port are not supported.
5. Send the token in an **`Authorization: Bearer …`** header on every request, including `/api/v1/info`. Revoke access from Settings when a client no longer needs it; there is no remote token-management endpoint.

Tokens can be issued while the listener is disabled. A **Never** expiry does not remove notebook or permission restrictions, and the token can still be revoked. Prefer a finite expiry and only the permissions the client needs.

!!! warning "Do not expose the embedded HTTP port"
    Keep VNote's listener on loopback. Do not publish or port-forward its HTTP port to other machines. Remote use requires an administrator-managed HTTPS reverse proxy on the **same host**, following the upstream [HTTPS and Host/Origin rules](https://github.com/vnotex/vnote/blob/v4.14.4/docs/http-api.md#https-for-other-machines). VNote does not provide TLS, a browser interface, or CORS: requests with `Origin` or `Cookie` headers are rejected. Do not use a browser-based OpenAPI “try it” client.

## Permissions and note boundaries

| Scope | Allows |
| --- | --- |
| `notes:read` | List granted open notebooks and their nodes, read metadata and saved content, and search saved notes. |
| `notes:read-live` | Additionally read the active editor's live content with `view=live`; also requires `notes:read`. |
| `notes:write` | Create an empty Markdown/text note, replace or append content, and rename supported notes. |
| `notes:trash` | Move supported ordinary notes to reversible trash; separate from write permission. |

Grants name specific notebooks, not arbitrary filesystem paths. Both **raw** and **bundled** notebooks support authorized reads and supported Markdown/text mutations, but only while open. Use the stable notebook/node IDs returned by the API, not a path constructed from a displayed name. Removing and re-adding a raw notebook is not identity-preserving.

- **Protected/encrypted notes** are omitted from API listings and search, including their names and snippets, even when unlocked in an editor. The API cannot unlock them.
- **Specialized or binary notes** may expose metadata without readable content. Check capability flags rather than assuming every file type can be read or changed.
- **Saved reads and search** use persisted content, not unsaved editor text. A live read needs the additional permission, returns `dirty`, and does not save the editor. If no active writer is available, the response explicitly falls back to `view=saved`.
- **Dirty editors** are not silently saved or overwritten by API mutations. Resolve `unsaved_changes` with the note's owner before attempting a new change.
- **Trash is reversible only**. Raw notebooks report `capabilities.trash=false`; an otherwise valid DELETE can be accepted with `202` and later fail with `unsupported_trash` (`422`), `committed=false`, and `saved=false`. There is no permanent-delete fallback.

## Read-only PowerShell example

With the listener enabled and a read-only token issued, run this in PowerShell. Paste the token into the hidden prompt, not into the command itself. Both requests are **GET** requests: they report API information and list the granted notebooks currently open without changing notes.

```powershell
$secret = Read-Host 'VNote client token' -AsSecureString
$headers = @{
    Authorization = 'Bearer ' + [System.Net.NetworkCredential]::new('', $secret).Password
}
try {
    Invoke-RestMethod -Method Get -Uri 'http://127.0.0.1:18765/api/v1/info' -Headers $headers
    Invoke-RestMethod -Method Get -Uri 'http://127.0.0.1:18765/api/v1/notebooks' -Headers $headers
}
finally {
    $secret.Dispose()
    Remove-Variable secret, headers
}
```

Adjust the port if you changed it in Settings. The authorization header necessarily contains the plaintext token in process memory; removing variables is not a guarantee of memory erasure. The example does not persist the token or put it in command history. Do not log request headers, and clear the clipboard if you pasted the token from it.

## Writes, conflicts, and operation results

For clients that need write access, consult the full [endpoint and conflict contract](https://github.com/vnotex/vnote/blob/v4.14.4/docs/http-api.md#validators-and-conflict-recovery) before implementing mutations. Existing-note changes require a strong, quoted `If-Match` value from the response payload:

| Action | Required validator |
| --- | --- |
| Replace or append content | `contentVersion` from a **saved** content read. |
| Rename | `metadataVersion` from metadata. |
| Trash | `noteStateVersion` from saved content. |

The HTTP `ETag` describes a response page, not the full-note mutation validator. Do not substitute it, a live-content validator, or a filename. Creating a note creates an **empty** note; initializing its content is a separate conditional operation, not an atomic create-with-content request.

**`202 Accepted` is not success.** Poll the returned `Location` with the same token until the operation reaches a terminal state, then inspect `committed`, `saved`, and any error. A failed operation can still have changed content in memory or saved it to disk; failure does not imply rollback. A version conflict (`412`) requires a fresh read and reconciliation; an unsaved-editor conflict (`409`) requires the owner to resolve the editor. Do not blindly retry mutations after a timeout, lost response, restart, or expired operation record: the original change may already have taken effect.

## Storage and revocation

Only the listener's `enabled`, `address`, and `port` settings are stored under `httpApi` in local **`session.json`**. HTTP API keys in **`vnotex.json` are ignored, not migrated**. Neither file stores bearer secrets or provides a token-management workflow.

The owner-protected credential registry stores **SHA-256 verifiers**, not recoverable bearer secrets. On Windows it is `%LOCALAPPDATA%/VNote/http-api/tokens.json`; portable Windows profiles use `config/local/http-api/tokens.json` beside the executable. Other platforms use their application-data profile, not a cache. This is separate from ordinary settings and is not cryptographic machine binding: deliberately copying a valid registry can make its tokens usable elsewhere. Do not share it with a notebook or edit it to revoke a client.

Use **Settings → HTTP API** to revoke tokens. Revocation takes effect in memory immediately; if persistence fails, VNote stops the listener and reports the error. Fix the storage/protection problem before enabling the listener again—do not assume the failed revocation was durably saved. Disabling the listener is not the same as revoking a token.

## Related workflows

- Use [Tasks](tasks.md) to run trusted local programs; the HTTP API does not expose shell commands or notebook tasks.
- Use [Notebook Sync](../managing-notes/notebook-sync.md) for synchronization; the API does not expose sync controls.
- For access auditing, limits, supported endpoints, and error codes, use the [version-pinned upstream guide](https://github.com/vnotex/vnote/blob/v4.14.4/docs/http-api.md).

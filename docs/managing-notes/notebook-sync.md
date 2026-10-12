# Notebook Sync

A notebook is a directory of files that you can keep in sync across machines. Bundled notebooks support built-in **Git**, **WebDAV** (including Nextcloud), and **Jianguoyun (WebDAV)** sync; both bundled and raw notebooks can also use a folder-sync service. Ordinary notes remain directly readable files, while [encrypted notes](encrypted-notes.md) require VNote, their keys, and the master password.

## Choose a sync method

| Method | Remote storage | Authentication |
| --- | --- | --- |
| Git | A normal Git repository | Personal Access Token (PAT); Git user name where required |
| WebDAV / Nextcloud | Ordinary notebook files in a dedicated existing collection | Username and password or app password |
| Jianguoyun (WebDAV) | VNote-managed versioned storage, not cloud-editable notebook files | Jianguoyun username and app password |
| Folder-sync service | A synchronized copy of the local folder | Managed by your sync client |

## Configure built-in sync

For a new **bundled notebook**, choose **Sync method** in **New Notebook**, then click **Configure** before creating it. For an existing notebook, use the notebook panel's **Sync Info** entry to configure synchronization. **Manage Notebooks** shows the current method as read-only text. Raw notebooks do not support built-in sync.

### Built-in Git sync

VNote handles cloning, committing, fetching, and pushing without leaving the application. Create the remote repository first; for a new notebook, start with an empty repository on your Git host. Enter:

- **Remote URL** — an HTTPS Git URL (for example `https://github.com/user/repo.git`) or a `file://` URL such as `file:///path/to/repo.git`.
- **Git user name** — the login of the PAT owner, not necessarily the repository owner. Gitee requires it; GitHub accepts it as optional. Changing only this username preserves local Git history.
- **Personal Access Token** — a token allowed to access the repository. For a classic GitHub PAT, private repositories require the `repo` scope.

### WebDAV and Nextcloud

1. Create a dedicated collection (folder) on the server for one notebook. It must already exist; do not point VNote at a shared account root containing unrelated data.
2. Choose **WebDAV**. Nextcloud uses this same method, not a separate backend: obtain the WebDAV URL from your Nextcloud account and use the URL of the notebook's dedicated collection.
3. Enter **Collection URL**, **Username**, and **Password or app password**, then apply the configuration.

The collection URL must be an absolute HTTP or HTTPS URL with a host and a valid path, without embedded credentials, a query string, or a fragment. VNote keeps ordinary notebook files on this remote; empty remote folders may be retained rather than recursively removed.

!!! warning "Prefer HTTPS"
    Plain HTTP exposes your credentials and notebook data in transit. Use HTTPS even when some note bodies are encrypted: metadata, separate assets, and credentials still need transport protection.

The server must support safe conditional writes. Setup errors may identify a failed WebDAV check, an HTTP status, or missing or weak ETags (the server's file-version identifiers). Check the collection URL, permissions, credentials, and server compatibility against that message; do not bypass conditional-write checks or blindly overwrite the collection to make setup succeed.

### Jianguoyun (WebDAV)

1. Create a dedicated Jianguoyun folder for the notebook and obtain an **app password** from Jianguoyun.
2. Choose **Jianguoyun (WebDAV)**, not generic WebDAV.
3. Set **Collection URL** to an HTTPS collection such as `https://dav.jianguoyun.com/dav/vnote-notebook/`. The `/dav/` account root is not accepted.
4. Enter **Username** and **App password**. Use the app password, not your account password, and apply the configuration.

!!! warning "Managed remote storage"
    Jianguoyun stores VNote-managed versions, not ordinary notebook files for cloud-side editing. Do not edit that storage in the cloud or reuse the collection for a different sync method. Remote history and deleted data are retained, are not automatically removed, and can increase storage use. Disabling sync does not delete them.

### Credentials and changing methods

Sync secrets are stored per notebook in the device's operating-system credential store, not in notebook settings. Configure credentials on each device; copying a notebook does not copy its stored sync password or PAT. If secure credential storage is unavailable, resolve that error rather than putting secrets in notebook JSON.

**Sync Info** lets you update credentials. Secret fields are never prefilled; when the dialog says **Leave blank to keep existing**, an empty field preserves the saved secret. Changing a WebDAV/Jianguoyun username requires a new password or app password.

To switch backends, first finish any conflicts or pending recovery, then use **Disable Sync** before selecting the new method. Changing the URL also requires confirmation and retires or rebuilds local sync state. Disabling sync removes this device's stored credentials but preserves working files and recovery data; it does not remove remote data. Do not mix provider-specific recovery archives or remove them to bypass a blocked reconfiguration.

## Open an existing notebook from a remote

Use **Open Notebook → Remote URL**:

1. Select the same **Sync method** used to publish the notebook.
2. Enter the remote repository or collection URL and the credentials described above. The Git login field here is labeled **Git username**.
3. Choose a **Local root folder** that does **not exist yet**, inside an existing parent folder.
4. Open the notebook. Git clones its repository; WebDAV downloads its notebook files; Jianguoyun downloads the notebook from its VNote-managed storage.

Git and generic WebDAV can download anonymously only if the server permits it. Leave the Git PAT empty, or both WebDAV credentials empty, for this mode: the downloaded notebook remains editable, but sync is inactive until you add credentials. Jianguoyun always requires both username and app password; anonymous download is not supported.

## Sync as you work

Use the notebook panel's **Sync Now** button to synchronize immediately and **Sync Info** to inspect its state or settings. While synchronization is running, the sync button can cancel it; allow cancellation or recovery to finish before starting another operation.

You can also enable **auto-sync** in **Settings → Sync**. The **Auto-sync interval** controls how often background sync may run (set it to `0` / *Immediate* to sync on every change).

## Conflicts and recovery

Sync before and after a writing session, and wait for incoming changes before editing on another machine. Avoid editing the same note on two machines before synchronization finishes.

For Git and generic WebDAV, **Resolve Sync Conflicts** offers **Keep local**, **Keep remote**, and, where supported, **Keep both**. These select complete versions, including deletions; **Keep both** preserves ordinary files without merging their text. Metadata and protected files require a single complete version, so **Keep both** is unavailable for those entries. Choosing one notebook or folder index can leave other retained files unindexed; inspect the notebook's [external files](notebooks-folders-notes.md#the-index-and-external-files) afterward.

Jianguoyun conflicts are **whole-version** choices, not a line-by-line merge or independent selection of individual note files. Review which version you intend to keep before accepting. Encrypted notes and their key data must stay together; do not combine a payload from one version with keys from another.

WebDAV keeps journaled recovery data, and Jianguoyun supports resuming interrupted operations. If VNote reports unfinished recovery or an interrupted backend change, preserve the notebook and recovery archives, follow the reported recovery guidance, and finish recovery before changing the method/URL or syncing again. Do not delete journals, key files, or recovery backups as a troubleshooting shortcut.

## Folder-sync services

If you prefer not to use built-in sync — or you are syncing a raw notebook — you can rely on a folder-sync service instead. With the default folder settings, a bundled notebook keeps its notes, images, attachments, index, and encryption keys under its **Notebook Root Folder**. A raw notebook is simply the folder itself; VNote keeps its metadata and cache in the application data folder, so each machine maintains its own record of it.

The general pattern is:

1. Place the Notebook Root Folder inside a directory managed by your sync tool.
2. On each computer, **open** that folder as a notebook (see [Importing & Migrating](importing-migrating.md)).
3. Edit as usual; your sync tool propagates the file changes between machines.

Examples include **Dropbox**, **OneDrive**, **Nextcloud**, and **Google Drive**. Nextcloud's desktop folder sync is an alternative to VNote's built-in WebDAV method; choose one synchronization mechanism for the same working notebook rather than letting two compete.

!!! tip "Let sync settle before editing"
    When you switch machines, let the sync client finish downloading before you start editing. If it produces conflicting copies, preserve them until you have compared and recovered the needed content. Do not hand-merge encrypted files or key metadata; follow the [encrypted-note recovery guidance](encrypted-notes.md#backup-and-recovery).

## What gets synced

Keep the notebook root's contents together, including the bundled notebook's index, configuration, and complete encryption key hierarchy. If you configured assets or a recycle bin outside the root, a root-folder copy does not include those external paths; account for them separately in your backup or migration setup. Keep the encryption master password safe as well — it is not replaced by your sync credentials.

Application-wide settings are stored separately in VNote's [configuration folder](../customization/settings.md) and are not part of a notebook. For moving a notebook rather than ongoing synchronization, see [Importing & Migrating](importing-migrating.md).

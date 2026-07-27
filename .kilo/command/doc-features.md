---
description: Sync docs with new code commits and record the synced code commit
---

# doc-features

Keep this documentation repo in sync with the VNote **code** repo, and record
exactly which code commit the docs currently reflect.

## Repos

- **Docs repo** (this repo, current working directory): the MkDocs Material site.
- **Code repo**: `https://github.com/vnotex/vnote`. **Clone it fresh into a temp folder** and
  read its history from there. Never modify the docs repo's working tree while
  cloning — clone to a path outside this repo (e.g.
  `$env:TEMP\vnote-code-<random>`).

## Sync marker

The code commit the docs currently reflect is stored in the tracked file
`.docs-code-sync` at the docs repo root. It contains a single line: the full
40-char code-repo commit SHA.

- If `.docs-code-sync` is **missing**, do not guess. Stop and ask the user which
  code commit the docs are currently up to date with (or whether to initialize
  it to the cloned code repo's current HEAD), then create the file with that SHA.

## Arguments

`$ARGUMENTS` — an optional **target** code commit (SHA, tag, or ref) to sync up
to. If empty, use the current tip of the code repo's default branch.

## Workflow

1. **Read the current synced commit** from `.docs-code-sync` (call it `FROM`).
2. **Clone the code repo into a temp folder** (shallow, enough history to cover
   the range — depth 100 is enough):
   `git clone --depth 100 https://github.com/vnotex/vnote "$env:TEMP\vnote-code"`.
   If `FROM` is not present in the shallow clone (range spans more than ~100
   commits), deepen with `git -C "$env:TEMP\vnote-code" fetch --deepen 100`
   (repeat as needed) or re-clone with a larger depth. Clean up the temp folder
   when done.
3. **Resolve the target** (call it `TO`): `$ARGUMENTS` if provided, otherwise the
   cloned default-branch tip (`HEAD`). Resolve both `FROM` and `TO` to full SHAs
   in the temp clone.
4. **List new commits** in the range with:
   `git -C "$env:TEMP\vnote-code" log --no-merges --stat FROM..TO`.
   If the range is empty, report that docs are already up to date and stop.
5. **Assess each new commit** for user-facing documentation impact. Docs likely
   need updating/creating when a commit adds or changes: features, settings/
   config keys, keyboard shortcuts, UI/menus, CLI flags, file formats, or default
   behavior. Skip pure refactors, tests, CI, build tooling, and internal-only
   changes.
6. **Report a plan** first: for each doc-relevant commit, list the SHA + subject
   and the concrete docs pages to create or edit (English `foo.md` and its
   Chinese sibling `foo.zh.md`, per this repo's i18n conventions in `AGENTS.md`).
7. **Apply the doc changes** following this repo's authoring conventions
   (no hard-wrapped prose, `.zh.md` counterparts, `nav_translations` for new nav
   entries). Validate with `.\.venv\Scripts\mkdocs.exe build --strict`
   (must be 0 warnings).
8. **Advance the marker**: write the resolved `TO` SHA into `.docs-code-sync`.
9. **Commit** (only when the user has approved committing): stage the changed
   docs plus `.docs-code-sync` and commit with a message noting the code range,
   e.g. `docs: sync to vnote <TO-short> (from <FROM-short>)`. Follow the repo
   convention of a night-time author/commit date.

## Notes

- Keep the marker update and the docs changes in the **same** commit so the
  recorded code commit always matches the docs state.
- If a new code commit needs docs but the correct content is ambiguous, ask the
  user rather than inventing behavior.

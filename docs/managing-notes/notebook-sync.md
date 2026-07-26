# Notebook Sync

VNote has no built-in cloud account, and that is by design. Because a notebook is an ordinary directory of plain files, you can sync it with whatever service or tool you already trust — and keep full control of your data. See [Why VNote](../getting-started/why-vnote.md) for the philosophy behind this.

## How syncing works

A notebook is entirely contained in its **Notebook Root Folder**: notes, images, attachments, and configuration all live inside it. To sync a notebook, you sync that folder. There is no central database to reconcile — the file system *is* the source of truth.

The general pattern is:

1. Place the Notebook Root Folder inside a directory managed by your sync tool.
2. On each computer, **import** that folder as a notebook (see [Importing & Migrating](importing-migrating.md)).
3. Edit as usual; your sync tool propagates the file changes between machines.

## Folder-sync services

Services such as **Dropbox**, **OneDrive**, **Nextcloud**, **Google Drive**, or any folder-sync utility work well. Keep the notebook inside the synced directory on every machine and let the service move files around. This is the simplest option and needs no extra tooling.

!!! tip "Let sync settle before editing"
    When you switch machines, give the sync client a moment to finish downloading before you start editing. Editing a notebook on two machines at once, before changes have synced, is what leads to conflicts.

## Version control with git

For full history and fine-grained control, track a notebook with **git**. Because notes are plain text, git shows meaningful line-by-line diffs, and you get a complete, revertible history of your knowledge base. Initialize a repository in the Notebook Root Folder, commit as you go, and push to any remote you like.

Git also gives you explicit conflict handling if two machines diverge, which some users prefer over silent folder-sync merges.

## Avoiding and resolving conflicts

- **Sync before and after a session.** Make sure the notebook is up to date before you start, and let changes upload before you leave.
- **Don't edit the same note on two machines at once.** Conflicts happen when the same file changes in two places before syncing.
- **If a conflict occurs,** your sync tool will usually keep both versions (for example, a "conflicted copy" file). Open both, merge the content by hand in VNote, and delete the extra file. With git, resolve the conflict as you would for any text file.

## What gets synced

Everything under the Notebook Root Folder, including VNote's per-notebook index and configuration, is part of the notebook and should be synced together. Application-wide settings are stored separately in VNote's [configuration folder](../customization/settings.md) and are not part of a notebook — sync those only if you also want to carry your app settings between machines.

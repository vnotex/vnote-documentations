# Notebook Sync

Because a notebook is an ordinary directory of plain files, you can keep it in sync across machines in more than one way. VNote has a **built-in Git sync** for bundled notebooks, and — since everything is plain text — you can equally rely on any folder-sync service you already trust. Either way you keep full control of your data. See [Why VNote](../getting-started/why-vnote.md) for the philosophy behind this.

## Built-in Git sync

Bundled notebooks can synchronize themselves through Git, without leaving VNote. VNote handles cloning, committing, fetching, and pushing for you, and stores the remote credentials per notebook.

### Enable sync on a new notebook

In the **New Notebook** dialog (bundled type), set **Sync method** to **Git**, then click **Configure...** to enter the remote details before the notebook is created:

- **Remote URL** — an HTTPS git URL (for example `https://github.com/user/repo.git`) or a `file://` path.
- **Personal Access Token (PAT)** — used to authenticate against the remote. For GitHub this is a token with the `repo` scope.

### Clone an existing notebook from a remote

To pick up a notebook that already lives on a remote, use **Open Notebook** and choose **Remote URL**:

1. Enter the **Remote URL** and, optionally, a **Personal Access Token**. Leaving the PAT empty opens the notebook without syncing yet.
2. Choose a **Local root folder** to clone into (it must not exist yet, or be empty).
3. VNote clones the repository and opens it as a notebook.

### Sync as you work

Each bundled notebook shows a **Sync** button in the notebook title bar:

- Click **Sync Now** to synchronize immediately.
- The **Sync Info** menu entry opens a dialog where you can review sync state, add or update the **Personal Access Token**, and reconfigure the remote.

You can also enable **auto-sync** in **Settings → Sync**. The **Auto-sync interval** controls how often background sync may run (set it to `0` / *Immediate* to sync on every change).

### Resolving conflicts

If the same file changed on two machines, VNote opens a **Resolve Sync Conflicts** dialog listing the affected files so you can choose how to resolve each one. Simple cases are reconciled automatically; the dialog appears only when a real conflict needs your decision.

## Folder-sync services

If you prefer not to use Git — or you are syncing a raw notebook — you can rely on a folder-sync service instead. A notebook is entirely contained in its **Notebook Root Folder**: notes, images, attachments, and configuration all live inside it. To sync a notebook this way, you sync that folder.

The general pattern is:

1. Place the Notebook Root Folder inside a directory managed by your sync tool.
2. On each computer, **open** that folder as a notebook (see [Importing & Migrating](importing-migrating.md)).
3. Edit as usual; your sync tool propagates the file changes between machines.

Services such as **Dropbox**, **OneDrive**, **Nextcloud**, **Google Drive**, or any folder-sync utility work well. Keep the notebook inside the synced directory on every machine and let the service move files around.

!!! tip "Let sync settle before editing"
    When you switch machines, give the sync client a moment to finish downloading before you start editing. Editing a notebook on two machines at once, before changes have synced, is what leads to conflicts.

## Avoiding and resolving conflicts

- **Sync before and after a session.** Make sure the notebook is up to date before you start, and let changes upload before you leave.
- **Don't edit the same note on two machines at once.** Conflicts happen when the same file changes in two places before syncing.
- **If a conflict occurs with a folder-sync service,** it will usually keep both versions (for example, a "conflicted copy" file). Open both, merge the content by hand in VNote, and delete the extra file. With the built-in Git sync, use the **Resolve Sync Conflicts** dialog instead.

## What gets synced

Everything under the Notebook Root Folder, including VNote's per-notebook index and configuration, is part of the notebook and should be synced together. Application-wide settings are stored separately in VNote's [configuration folder](../customization/settings.md) and are not part of a notebook — sync those only if you also want to carry your app settings between machines.

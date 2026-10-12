# Importing & Migrating

A VNote notebook is a directory of files, so existing notes can be imported and complete notebooks can be moved between computers. Optional [encrypted notes](encrypted-notes.md) also require their key hierarchy and master password. This page covers bringing content in; for keeping a notebook in sync across machines, see [Notebook Sync](notebook-sync.md).

## Build a notebook from an existing folder

The recommended way is to import your files into a **bundled notebook**, so that they gain everything the notebook index provides — [tags](tags.md), attachments, the recycle bin, optional [note-body encryption](encrypted-notes.md), and built-in [Git, WebDAV, and Jianguoyun sync](notebook-sync.md):

1. Choose **New Notebook**, leave **Type** set to **Bundled notebook**, and point it at an empty folder (a bundled notebook's root folder must be empty).
2. Select the notebook or a folder in it, then choose **Import Folder** from the **New** menu in the toolbar and pick your existing directory. Your files are copied in as folders and notes.

You can also copy files straight into the Notebook Root Folder from outside VNote. They then appear as [external files](notebooks-folders-notes.md#the-index-and-external-files) that you adopt with **Import to Index** — or that VNote adopts for you the first time you open one, as long as **Import External Files on Open** is enabled. For a deep directory tree, **Import Folder** is less work, because adopting external folders happens one level at a time.

### When a raw notebook is the better fit

For a hands-on example, [open the demo notebook](../getting-started/quick-start.md#try-the-demo-notebook) from this documentation repository. The Notebooks panel menu also offers **Open Folder As Raw Notebook**: select `demo-notebook/` to browse it in place, without copying files. This is not **Import Folder** or **Open Notebook**; the latter opens a bundled notebook.

Choose **Type → Raw notebook** and point VNote at your directory when the folder should be adopted as it stands:

- Nothing is imported or restructured, and no VNote configuration file is written into the folder — VNote browses it in place, much like a file browser.
- This is the right choice when the folder's structure is maintained outside VNote — by another tool, a script, or a shared repository — and that layout should stay authoritative.

A raw notebook is not read-only: creating, renaming, moving, and importing notes, or pasting an image, all write to the folder as usual. What it avoids is a one-off migration of what is already there.

The trade-off is that a raw notebook has no index, so tags, attachments, the recycle bin, note-body encryption, and built-in sync are unavailable. See [Notebooks, Folders & Notes](notebooks-folders-notes.md#which-type-should-i-use) for the full comparison.

## Import an existing notebook

Open an existing bundled notebook by pointing VNote at its root, keeping its configuration and encryption keys intact:

1. Choose **Open Notebook** and select its **Notebook Root Folder**.
2. VNote reads the notebook's configuration files and restores it — its folders, notes, and settings reappear as before.

This is how you pick up a notebook that was created on another machine or restored from a backup. A raw notebook has no configuration in its folder, so you pick one up the same way you created it: **New Notebook** with **Type → Raw notebook**, pointed at the directory.

## Import files and folders into a notebook

You can pull external content into an existing notebook without leaving VNote. Select the target notebook or folder in the Notebooks panel, then use the **New** menu in the toolbar:

- **Import Files** — copy individual external files in as notes.
- **Import Folder** — copy an entire external directory tree in, recursively (hidden entries are skipped).

Imported items are placed under the selected location in the notebook.

## Share a folder

**Share Folder**, in the notebook explorer context menu, creates *a portable copy of this folder including metadata*. Use it to hand a slice of a notebook to someone else, or to import it into another notebook while retaining supported metadata.

The action is available on an indexed folder of a **bundled** notebook that is not the notebook root. The result is an ordinary folder you can copy, zip or email — the folder's content plus a parallel `vx.json` metadata subtree — not an archive format of its own.

A few details worth knowing:

- Notes you have open are saved first, so the copy always carries their latest content.
- Symbolic links, junctions and reparse points are not followed; VNote refuses them rather than duplicating what they point at.
- If two names would collide on a case-insensitive filesystem, you are warned up front.
- The copy is verified before it is published, so a failed share leaves nothing half-written behind.

If the shared folder contains encrypted notes, keep the entire produced folder and its key metadata together. The recipient needs the source master password to import it. This does not encrypt separate assets, comments, or visible metadata; see [Encrypted Notes](encrypted-notes.md).

## Import a shared folder

**New → Import Folder** in the toolbar opens the **Import Folder** dialog, which has two modes:

- **External folder** — an ordinary folder from disk. Its notes are indexed as new notes, with fresh ids and timestamps.
- **Shared folder from VNote** — a folder produced by **Share Folder**; the path field's placeholder says exactly that, *Folder produced by Share Folder*. Note ids, dates, tags and attachments are preserved, so the folder keeps its history as it travels between notebooks.

The shared-folder mode needs a destination in a **writable bundled** notebook; raw notebooks and read-only notebooks are rejected, because there is no index to preserve the metadata in.

Everything is validated before a single file is copied, and a failed or cancelled import leaves the notebook exactly as it was. Duplicate note ids, names that would collide, and re-importing a folder that is already in the notebook are refused rather than merged or overwritten.

### Import encrypted shared notes

Shared-folder import supports encrypted Markdown, text, and mind-map notes. Before importing, the destination bundled notebook must already have encryption initialized; if necessary, [create or encrypt a supported note](encrypted-notes.md) there first.

1. Choose **Shared folder from VNote** and select the complete shared folder.
2. If the destination is locked, enter its password in **Unlock Destination Notebook**.
3. Enter the source notebook's master password in **Unlock Encrypted Bundle** when requested. Import authenticates the source and protects the imported bodies with the destination keys.
4. Wait for the import result. Cancelling the source-password prompt leaves the destination unchanged; do not copy individual encrypted files into place to bypass authentication.

For transfers between notebooks already open in VNote, see [Copy and move between notebooks](notebooks-folders-notes.md#copy-and-move-between-notebooks).

## Open a VNote 3 notebook

VNote can read notebooks created by VNote 3. Choose **Open Notebook** and click **Open V3 Notebook** in that dialog, then point it at the old notebook's folder. See [Data Migration](../help/data-migration.md).

## Migrating a notebook to another computer

With the default storage paths, migrate a bundled notebook by copying its complete root folder:

1. Copy the entire Notebook Root Folder to the other machine (via a USB drive, a synced folder, or Git), including configuration and encryption keys. Preserve the master password for any encrypted notes.
2. On the other machine, **open** that folder as a notebook. Enter the master password when opening protected content, and configure sync credentials separately on that device if needed.

Custom asset or recycle-bin paths outside the root are not part of this copy; include them separately and make sure the destination paths are appropriate. See [Encrypted Notes](encrypted-notes.md#backup-and-recovery) before restoring protected content from a backup.

A raw notebook carries only your files. Copying the folder brings the content across, but the other machine opens it as a new raw notebook and builds its own local record of it.

A common setup is to keep the Notebook Root Folder inside a directory that a third-party service synchronizes — such as Dropbox or OneDrive — and open it on each computer. You then edit and manage your notes in VNote while the files are synchronized by a service you already trust. See [Notebook Sync](notebook-sync.md) for details and for VNote's built-in Git, WebDAV, and Jianguoyun sync, including opening a notebook directly from a remote.

## Migrating from other applications

VNote does not include built-in importers for other note apps, but because it works with plain Markdown and images, exporting from another tool to Markdown is usually enough to bring your content over. See [Data Migration](../help/data-migration.md) for tips on migrating from specific tools.

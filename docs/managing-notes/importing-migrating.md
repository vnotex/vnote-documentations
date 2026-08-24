# Importing & Migrating

Because a VNote notebook is just a directory of plain files, moving existing notes into VNote — or moving a VNote notebook between computers — is straightforward. This page covers bringing content in; for keeping a notebook in sync across machines, see [Notebook Sync](notebook-sync.md).

## Build a notebook from an existing folder

The recommended way is to import your files into a **bundled notebook**, so that they gain everything the notebook index provides — [tags](tags.md), attachments, the recycle bin, and built-in [Git sync](notebook-sync.md):

1. Choose **New Notebook**, leave **Type** set to **Bundled notebook**, and point it at an empty folder (a bundled notebook's root folder must be empty).
2. Select the notebook or a folder in it, then choose **Import Folder** from the **New** menu in the toolbar and pick your existing directory. Your files are copied in as folders and notes.

You can also copy files straight into the Notebook Root Folder from outside VNote. They then appear as [external files](notebooks-folders-notes.md#the-index-and-external-files) that you adopt with **Import to Index** — or that VNote adopts for you the first time you open one, as long as **Import External Files on Open** is enabled. For a deep directory tree, **Import Folder** is less work, because adopting external folders happens one level at a time.

### When a raw notebook is the better fit

Choose **Type → Raw notebook** and point VNote at your directory when the folder should be adopted as it stands:

- Nothing is imported or restructured, and no VNote configuration file is written into the folder — VNote browses it in place, much like a file browser.
- This is the right choice when the folder's structure is maintained outside VNote — by another tool, a script, or a shared repository — and that layout should stay authoritative.

A raw notebook is not read-only: creating, renaming, moving, and importing notes, or pasting an image, all write to the folder as usual. What it avoids is a one-off migration of what is already there.

The trade-off is that a raw notebook has no index, so tags, attachments, the recycle bin, and built-in Git sync are unavailable. See [Notebooks, Folders & Notes](notebooks-folders-notes.md#which-type-should-i-use) for the full comparison.

## Import an existing notebook

A bundled notebook is a self-contained directory, so importing one is a matter of pointing VNote at its root:

1. Choose **Open Notebook** and select its **Notebook Root Folder**.
2. VNote reads the notebook's configuration files and restores it — its folders, notes, and settings reappear as before.

This is how you pick up a notebook that was created on another machine or restored from a backup. A raw notebook has no configuration in its folder, so you pick one up the same way you created it: **New Notebook** with **Type → Raw notebook**, pointed at the directory.

## Import files and folders into a notebook

You can pull external content into an existing notebook without leaving VNote. Select the target notebook or folder in the Notebooks panel, then use the **New** menu in the toolbar:

- **Import Files** — copy individual external files in as notes.
- **Import Folder** — copy an entire external directory tree in, recursively (hidden entries are skipped).

Imported items are placed under the selected location in the notebook.

## Share a folder

**Share Folder**, in the notebook explorer context menu, creates *a portable copy of this folder including metadata*. Use it to hand a slice of a notebook to someone else, or to move it into another notebook without losing anything.

The action is available on an indexed folder of a **bundled** notebook that is not the notebook root. The result is an ordinary folder you can copy, zip or email — the folder's content plus a parallel `vx.json` metadata subtree — not an archive format of its own.

A few details worth knowing:

- Notes you have open are saved first, so the copy always carries their latest content.
- Symbolic links, junctions and reparse points are not followed; VNote refuses them rather than duplicating what they point at.
- If two names would collide on a case-insensitive filesystem, you are warned up front.
- The copy is verified before it is published, so a failed share leaves nothing half-written behind.

## Import a shared folder

**New → Import Folder** in the toolbar opens the **Import Folder** dialog, which has two modes:

- **External folder** — an ordinary folder from disk. Its notes are indexed as new notes, with fresh ids and timestamps.
- **Shared folder from VNote** — a folder produced by **Share Folder**; the path field's placeholder says exactly that, *Folder produced by Share Folder*. Note ids, dates, tags and attachments are preserved, so the folder keeps its history as it travels between notebooks.

The shared-folder mode needs a destination in a **writable bundled** notebook; raw notebooks and read-only notebooks are rejected, because there is no index to preserve the metadata in.

Everything is validated before a single file is copied, and a failed or cancelled import leaves the notebook exactly as it was. Duplicate note ids, names that would collide, and re-importing a folder that is already in the notebook are refused rather than merged or overwritten.

## Open a VNote 3 notebook

VNote can read notebooks created by VNote 3. Choose **Open Notebook** and click **Open V3 Notebook** in that dialog, then point it at the old notebook's folder. See [Data Migration](../help/data-migration.md).

## Migrating a notebook to another computer

Since everything a bundled notebook needs lives under its root folder, migration is a copy:

1. Copy the Notebook Root Folder to the other machine (via a USB drive, a synced folder, or git).
2. On the other machine, **open** that folder as a notebook.

A raw notebook carries only your files. Copying the folder brings the content across, but the other machine opens it as a new raw notebook and builds its own local record of it.

A common setup is to keep the Notebook Root Folder inside a directory that a third-party service synchronizes — such as Dropbox or OneDrive — and open it on each computer. You then edit and manage your notes in VNote while the files are synchronized by a service you already trust. See [Notebook Sync](notebook-sync.md) for details and for VNote's built-in Git sync.

## Migrating from other applications

VNote does not include built-in importers for other note apps, but because it works with plain Markdown and images, exporting from another tool to Markdown is usually enough to bring your content over. See [Data Migration](../help/data-migration.md) for tips on migrating from specific tools.

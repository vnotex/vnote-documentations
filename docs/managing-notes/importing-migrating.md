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

## Migrating a notebook to another computer

Since everything a bundled notebook needs lives under its root folder, migration is a copy:

1. Copy the Notebook Root Folder to the other machine (via a USB drive, a synced folder, or git).
2. On the other machine, **open** that folder as a notebook.

A raw notebook carries only your files. Copying the folder brings the content across, but the other machine opens it as a new raw notebook and builds its own local record of it.

A common setup is to keep the Notebook Root Folder inside a directory that a third-party service synchronizes — such as Dropbox or OneDrive — and open it on each computer. You then edit and manage your notes in VNote while the files are synchronized by a service you already trust. See [Notebook Sync](notebook-sync.md) for details and for VNote's built-in Git sync.

## Migrating from other applications

VNote does not include built-in importers for other note apps, but because it works with plain Markdown and images, exporting from another tool to Markdown is usually enough to bring your content over. See [Data Migration](../help/data-migration.md) for tips on migrating from specific tools.

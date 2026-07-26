# Importing & Migrating

Because a VNote notebook is just a directory of plain files, moving existing notes into VNote — or moving a VNote notebook between computers — is straightforward. This page covers bringing content in; for keeping a notebook in sync across machines, see [Notebook Sync](notebook-sync.md).

## Build a notebook from an existing folder

If you already have a directory of Markdown files, you do not need to copy or restructure anything. Choose **New Notebook**, set **Type** to **Raw notebook**, and point VNote at that directory. VNote indexes the files that are already there without moving them.

This is the recommended way to start using VNote with an existing collection of notes.

## Import an existing notebook

A notebook is a self-contained directory, so importing one is a matter of pointing VNote at its root:

1. Choose **Open Notebook** and select its **Notebook Root Folder**.
2. VNote reads the notebook's configuration files and restores it — its folders, notes, and settings reappear as before.

This is how you pick up a notebook that was created on another machine or restored from a backup.

## Import files and folders into a notebook

You can pull external content into an existing notebook without leaving VNote. From a notebook or folder's context menu, import:

- **Files** — copy individual external files in as notes.
- **Folders** — copy an entire external directory tree in.

Imported items are placed under the selected location in the notebook.

## Migrating a notebook to another computer

Since everything the notebook needs lives under its root folder, migration is a copy:

1. Copy the Notebook Root Folder to the other machine (via a USB drive, a synced folder, or git).
2. On the other machine, **open** that folder as a notebook.

A common setup is to keep the Notebook Root Folder inside a directory that a third-party service synchronizes — such as Dropbox or OneDrive — and open it on each computer. You then edit and manage your notes in VNote while the files are synchronized by a service you already trust. See [Notebook Sync](notebook-sync.md) for details and for VNote's built-in Git sync.

## Migrating from other applications

VNote does not include built-in importers for other note apps, but because it works with plain Markdown and images, exporting from another tool to Markdown is usually enough to bring your content over. See [Data Migration](../help/data-migration.md) for tips on migrating from specific tools.

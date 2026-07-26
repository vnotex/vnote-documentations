# Notebooks, Folders & Notes

VNote manages your writing with a simple, transparent hierarchy: **notebooks**, **folders**, and **notes**. This structure maps directly onto your file system, so what you see in VNote is exactly what exists on disk.

## The hierarchy

- A **notebook** is a self-contained container. On disk it is a directory called the **Notebook Root Folder**, which holds all of that notebook's notes and configuration.
- A **folder** groups related notes inside a notebook. It corresponds to a directory within the Notebook Root Folder, and folders can be nested to **infinite levels**.
- A **note** is a single file inside a folder — most often a Markdown (`.md`) file, but VNote can also open and edit other text files.

VNote keeps a few index files inside each notebook to track its notes. For this reason it is best to create, move, and rename notes **from within VNote** rather than editing the directory structure behind its back.

## Notebooks

A notebook is independent and self-explanatory: everything it needs lives under its root folder. This is what lets you copy, sync, or version a notebook as a single directory.

### Create a notebook

- **From an empty folder** — choose **New Notebook** and point VNote at an empty directory. This is the usual starting point.
- **From an existing folder** — if you already have a directory full of Markdown files, choose **New Notebook From Folder** to build a notebook around them without moving anything. See [Importing & Migrating](importing-migrating.md).

### Open and close notebooks

Notebooks you have created or imported appear in the notebook selector on the left. Closing a notebook only removes it from the list in VNote; the files on disk are untouched, and you can import it again at any time.

## Folders

Right-click a notebook or an existing folder in the navigation panel to create a **New Folder**. Because nesting is unlimited, you can model anything from a flat list of notes to a deep, structured knowledge base. Folders can be renamed, moved, and deleted from the same context menu.

## Notes

Select a notebook or folder and choose **New Note** to create one. Name it with a `.md` suffix for Markdown. From the note's context menu you can rename, move (cut and paste between folders), copy, delete, and export notes, as well as reveal the underlying file in your system file manager.

Deleting a note moves it to VNote's recycle bin inside the notebook, so it can be recovered until you empty it.

## Everything is just files

Because the hierarchy is nothing more than directories and text files, you stay in full control of your data:

- Back up a notebook by copying its folder.
- Track a notebook's history with git.
- Edit a note with another tool when you need to.

To keep VNote's index consistent, prefer doing structural changes (create, move, rename, delete) inside VNote. See [Notebook Sync](notebook-sync.md) for syncing across machines and [Tags](tags.md) for organizing notes across the folder tree.

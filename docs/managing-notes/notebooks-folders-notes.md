# Notebooks, Folders & Notes

VNote manages your writing with a simple, transparent hierarchy: **notebooks**, **folders**, and **notes**. This structure maps directly onto your file system, so what you see in VNote is exactly what exists on disk.

## The hierarchy

- A **notebook** is a container for your notes. On disk it is a directory called the **Notebook Root Folder**. A bundled notebook is self-contained — its notes *and* its configuration live inside that directory. A raw notebook is simply that directory of files; VNote keeps its record of the notebook in the application's data folder instead.
- A **folder** groups related notes inside a notebook. It corresponds to a directory within the Notebook Root Folder, and folders can be nested to **infinite levels**.
- A **note** is a single file inside a folder — most often a Markdown (`.md`) file, but VNote can also open and edit other text files.

A bundled notebook keeps an index of its notes inside the Notebook Root Folder. For this reason it is best to create, move, and rename notes **from within VNote** rather than editing the directory structure behind its back — although VNote does notice files that appear on disk and lets you adopt them, see [The index and external files](#the-index-and-external-files).

## Notebooks

A bundled notebook is independent and self-explanatory: everything it needs lives under its root folder. This is what lets you copy, sync, or version it as a single directory. A raw notebook contains only your own files, so it carries no VNote configuration with it.

### Create a notebook

Choose **New Notebook** to create one. In the dialog, pick the notebook **Type**:

- **Bundled notebook** — VNote keeps an index of the notebook's structure and metadata in a `vx_notebook` folder under the root. That index is what makes [tags](tags.md), attachments, the recycle bin, manual ordering, and built-in [Git sync](notebook-sync.md) possible. The root folder must be empty (or not exist yet); you bring existing files in afterwards. **This is the recommended type.**
- **Raw notebook** — VNote browses an existing folder the way a file browser does. There is no index: the folder on disk *is* the structure. Opening it changes nothing — your files are not copied, reorganized, or given any VNote configuration file. In exchange, everything that depends on the index is unavailable: no tags, no attachments, no recycle bin, and no built-in Git sync.

### Which type should I use?

Prefer a **bundled notebook**. If you already have a folder of notes, create a bundled notebook and [import](importing-migrating.md) that folder into it — your notes stay plain files, and you gain the full feature set.

Choose a **raw notebook** only when one of these applies:

- The existing layout has to stay authoritative: you want VNote to adopt the folder as it is, without importing or restructuring it.
- The folder's structure is maintained outside VNote — by another tool, a script, or a shared repository — and VNote is only one of the ways you look at it.

A raw notebook is not read-only. Once it is open, creating, renaming, moving, and importing notes, or pasting an image, all write to that folder just as they would in a bundled notebook. What a raw notebook avoids is a one-off migration of your existing structure, and any VNote configuration inside the folder.

| | Bundled | Raw |
| --- | --- | --- |
| [Tags](tags.md) | Yes | No |
| Attachments | Yes | No |
| Recycle bin | Yes | No |
| Built-in [Git sync](notebook-sync.md) | Yes | No |
| Manual ordering of folders and notes | Yes | No |
| Images and other assets | Yes | Yes |
| Editing, [search](../search/index.md), [export](../productivity/export.md) | Yes | Yes |
| Files added to the folder from outside VNote | Listed as external files; adopt them when you want | Appear immediately |
| Notebook configuration | Stored in the folder, travels with it | Kept locally by VNote, per machine |

### The index and external files

A bundled notebook's index records which files and folders belong to the notebook, together with their metadata. It lives in the `vx_notebook` folder inside the Notebook Root Folder, so it travels with the notebook whenever you copy or sync it.

Because the index is separate from the file system, VNote can tell the two apart. A file or folder that sits under the root folder without being in the index is listed as an **external file** — greyed out, above the indexed items in its folder — so you can see at a glance what the notebook has adopted and what it has not. VNote's own directories are never listed: hidden entries (names starting with `.`), the `vx_notebook` folder, the assets folder (when it is a plain folder name under the root, as the default `vx_assets` is), legacy `vx_images` / `vx_attachments` / `_v_images` / `_v_attachments` folders, and anything on the notebook's ignore list.

From an external item's context menu:

- **Import to Index** — adopt it into the notebook. Adopting a folder adds the folder itself; its contents then appear as external items inside it, ready to be adopted in turn.
- **Ignore** — add its name to the notebook's ignore list so that it is no longer listed.

Two entries in the Notebooks panel's title-bar menu control the behaviour:

- **Show External Files** — whether external items are listed at all.
- **Import External Files on Open** — adopt an external note automatically the first time you open it.

This is what makes it safe to copy files into the Notebook Root Folder from outside VNote and pick them up from within. For a whole directory tree, **Import Folder** is usually less work, because it brings the tree in recursively in one step — see [Importing & Migrating](importing-migrating.md). The reverse of adopting is **Remove from Notebook** on an indexed item: it drops the item from the index but leaves the file on disk.

### Open and close notebooks

Notebooks you have created or opened appear in the notebook selector on the left. Closing a notebook only removes it from the list in VNote; the files on disk are untouched, and you can open it again at any time.

## Folders

Right-click a notebook or an existing folder in the Notebooks panel to create a **New Folder**. Because nesting is unlimited, you can model anything from a flat list of notes to a deep, structured knowledge base. Folders can be renamed, moved, and deleted from the same context menu.

## Notes

Select a notebook or folder and choose **New Note** to create one. Name it with a `.md` suffix for Markdown. From the note's context menu you can rename, move (cut and paste between folders), copy, delete, and export notes, as well as reveal the underlying file with **Open Location** (or **Copy Path**).

A note can also have **attachments** — arbitrary files associated with it. Use the **Attachments** button in the note's toolbar to add, open, rename, or remove them. VNote copies each one into that note's subfolder under the notebook's assets folder and records it in the index, so attachments require a bundled notebook.

In a bundled notebook, deleting a note moves it to VNote's recycle bin inside the notebook, so it can be recovered until you empty it. Raw notebooks have no recycle bin.

## Everything is just files

Because the hierarchy is nothing more than directories and text files, you stay in full control of your data:

- Back up a notebook by copying its folder.
- Track a notebook's history with git.
- Edit a note with another tool when you need to.

To keep a bundled notebook's index consistent, prefer doing structural changes (create, move, rename, delete) inside VNote — or adopt what turns up on disk, as described in [The index and external files](#the-index-and-external-files). See [Notebook Sync](notebook-sync.md) for syncing across machines and [Tags](tags.md) for organizing notes across the folder tree.

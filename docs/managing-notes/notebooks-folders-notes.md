# Notebooks, Folders & Notes

VNote manages your writing with a simple, transparent hierarchy: **notebooks**, **folders**, and **notes**. This structure maps directly onto your file system, so what you see in VNote is exactly what exists on disk.

## The hierarchy

- A **notebook** is a container for your notes. On disk it is a directory called the **Notebook Root Folder**. With default folder settings, a bundled notebook is self-contained — its notes *and* its configuration live inside that directory. A raw notebook is simply that directory of files; VNote keeps its record of the notebook in the application's data folder instead.
- A **folder** groups related notes inside a notebook. It corresponds to a directory within the Notebook Root Folder, and folders can be nested to **infinite levels**.
- A **note** is a single file inside a folder — most often a Markdown (`.md`) file, but VNote can also open and edit other text files.

A bundled notebook keeps an index of its notes inside the Notebook Root Folder. For this reason it is best to create, move, and rename notes **from within VNote** rather than editing the directory structure behind its back — although VNote does notice files that appear on disk and lets you adopt them, see [The index and external files](#the-index-and-external-files).

## Notebooks

With default folder settings, a bundled notebook keeps its files, configuration, and any encryption keys under its root folder, so you can copy, sync, or version it as a directory. Preserve the master password as well if you use [encrypted notes](encrypted-notes.md). Custom asset or recycle-bin paths outside the root need separate backup. A raw notebook contains only your own files, so it carries no VNote configuration with it.

### Create a notebook

Choose **New Notebook** to create one. In the dialog, pick the notebook **Type**:

- **Bundled notebook** — VNote keeps an index of the notebook's structure and metadata in a `vx_notebook` folder under the root. Bundled notebooks provide [tags](tags.md), attachments, the recycle bin, manual ordering, optional [note-body encryption](encrypted-notes.md), and built-in [Git, WebDAV, and Jianguoyun sync](notebook-sync.md). The root folder must be empty (or not exist yet); you bring existing files in afterwards. **This is the recommended type.**
- **Raw notebook** — VNote browses an existing folder the way a file browser does. There is no index: the folder on disk *is* the structure. Opening it changes nothing — your files are not copied, reorganized, or given any VNote configuration file. In exchange, tags, attachments, the recycle bin, note-body encryption, and built-in sync are unavailable.

### Which type should I use?

Prefer a **bundled notebook**. If you already have a folder of notes, create a bundled notebook and [import](importing-migrating.md) that folder into it — ordinary notes stay plain files, and you gain the full feature set, including optional encryption.

Choose a **raw notebook** only when one of these applies:

- The existing layout has to stay authoritative: you want VNote to adopt the folder as it is, without importing or restructuring it.
- The folder's structure is maintained outside VNote — by another tool, a script, or a shared repository — and VNote is only one of the ways you look at it.

A raw notebook is not read-only. Once it is open, creating, renaming, moving, and importing notes, or pasting an image, all write to that folder just as they would in a bundled notebook. What a raw notebook avoids is a one-off migration of your existing structure, and any VNote configuration inside the folder.

| | Bundled | Raw |
| --- | --- | --- |
| [Tags](tags.md) | Yes | No |
| Attachments | Yes | No |
| Recycle bin | Yes | No |
| Built-in [Git / WebDAV / Jianguoyun sync](notebook-sync.md) | Yes | No |
| [Note-body encryption](encrypted-notes.md) | Markdown, text, and mind-map notes | No |
| Manual ordering of folders and notes | Yes | No |
| Images and other assets | Yes | Yes |
| Editing, [search](../search/index.md), [export](../productivity/export.md) | Yes; encrypted bodies have [search/export restrictions](encrypted-notes.md) | Yes |
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

**Share Folder** creates a portable copy of a folder, metadata included, that another notebook can import without losing note ids, dates or tags — see [Importing & Migrating](importing-migrating.md#share-a-folder).

## Copy and move between notebooks

To transfer notes or folders between **bundled notebooks**, use **Copy** or **Cut** in the source notebook, switch to the destination notebook/folder, then **Paste**. Cross-notebook transfers are not supported for raw notebooks.

Before a copy, VNote saves affected open-note edits and pending comments so the destination receives the current content. For a move, first save and **close every open note inside the affected items**, including notes in a selected folder. VNote shows progress and per-item results; review any failures or items reported as left at the source before retrying. Attachments remain associated with transferred notes.

Use [Share Folder and Import Folder](importing-migrating.md#share-a-folder) when sending a folder to another person or computer. For protected content, also follow the [encrypted-note transfer guidance](encrypted-notes.md#backup-and-recovery).

## Ordering

Items are shown in the order you arrange them. Drag a note or folder to move it, or choose **Sort** to reorder a whole level in one dialog. The dialog lists the items with **Name**, **Created** and **Modified** columns:

- Click a column header for a one-shot reorder by that column; clicking it again reverses the direction. It is a one-shot operation, not a live sort, so the result becomes your manual order.
- **Move to Top**, **Move Up**, **Move Down** and **Move to Bottom** adjust individual rows, and rows can be dragged.
- Moving or dragging a row after a header click clears the sort indicator: you are back to plain manual ordering.

When a name is too long for the panel, the tree scrolls horizontally rather than truncating it.

## Notes

Select a notebook or folder and choose **New Note** to create one. Name it with a `.md` suffix for Markdown. VNote proposes a default name that is not already taken, and remembers the [template](../editing/templates.md) you last used for that file type. From the note's context menu you can rename, move (cut and paste between folders), copy, delete, and export notes, as well as reveal the underlying file with **Open Location** (or **Copy Path**). **Open as Detached** opens the note in its own top-level window — see [Editor Basics](../editing/editor-basics.md#detached-windows).

### Attachments

A note can also have **attachments** — arbitrary files associated with it. Use the **Attachments** button in the note's toolbar to add, open, rename, or remove them. VNote copies each one into that note's subfolder under the notebook's assets folder and records it in the index, so attachments require a bundled notebook.

If files already exist in the note's attachment folder but are missing from the list, click **Scan** in the Attachments popup. This registers eligible unlisted files **in place**, without copying them again. It skips already registered attachments, comment data, an empty `.gitkeep`, and images tracked by the Markdown note.

Use **Rename** or `F2` to rename a selected attachment. On Windows, a separate rename dialog supports Chinese input; after a successful rename, the attachment list reopens with that file selected and focused.

### Recycle bin

Deleting an indexed note in a bundled notebook moves it to VNote's recycle bin. Use **Open Recycle Bin** from the notebook panel's menu to access it; **Empty Recycle Bin** removes its contents permanently. Raw notebooks have no recycle bin.

In **Manage Notebooks → Advanced → Recycle bin folder**, choose an absolute path or a path relative to the notebook root. An empty setting uses `vx_notebook/recycle_bin`. A custom bin outside the root is not included when you copy or synchronize just the notebook root.

**Settings → Note Management → Automatically clean recycle bins** enables permanent removal of entries older than **Recycle bin retention** (1–3650 days). Enable it only if that retention period fits your recovery needs: deleted notes remain recoverable only until the bin is emptied or cleanup removes them, not indefinitely.

A note written by an older VNote version keeps its pictures in a legacy `vx_images` or `_v_images` folder; VNote offers to migrate them into the assets folder when you open it — see [Legacy image folders](../editing/images-and-image-host.md#legacy-image-folders).

## Everything is just files

The notebook hierarchy remains directories and files, with optional encryption for supported note bodies:

- Back up the complete notebook folder, including configuration and encryption keys; include any custom external resource paths separately.
- Track a notebook's history with git.
- Edit ordinary notes with another tool when needed; open encrypted notes in VNote and preserve their master password.

To keep a bundled notebook's index consistent, prefer doing structural changes (create, move, rename, delete) inside VNote — or adopt what turns up on disk, as described in [The index and external files](#the-index-and-external-files). See [Notebook Sync](notebook-sync.md) for syncing across machines and [Tags](tags.md) for organizing notes across the folder tree.

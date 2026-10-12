# Quick Start

This page walks you from a fresh install to your first note in a few minutes. If you have not installed VNote yet, see [Installation](installation.md).

## Try the demo notebook

Prefer to explore an existing notebook first? The [documentation repository](https://github.com/vnotex/vnote-documentations) includes [`demo-notebook/`](https://github.com/vnotex/vnote-documentations/tree/main/demo-notebook), with English and Chinese examples of Markdown, task lists, tables, code, and links between notes.

1. Clone the repository, or choose **Code → Download ZIP** on GitHub and extract it.
2. Copy `demo-notebook/` to a writable location before experimenting; edits in VNote change the files on disk.
3. In VNote's **Notebooks** panel, open the three-dot menu and choose **Open Folder As Raw Notebook**, then select the copied `demo-notebook` folder, not the repository root.
4. Open `Welcome.md` (or `Welcome.zh.md` for Chinese), then follow its links to **Markdown Tour** and **Projects/Release Plan**.

This opens the folder in place as a **raw notebook**; it does not copy or migrate its files. Do not use **Open Notebook**, which expects a bundled notebook. The `.zh.md` files are Chinese examples alongside the English notes, not language packs. For tags, attachments, the recycle bin, encryption, or built-in sync, use a bundled notebook instead; see [Importing & Migrating](../managing-notes/importing-migrating.md#when-a-raw-notebook-is-the-better-fit).

![The demo notebook open in VNote, with Welcome in read mode and its notes in the notebook tree](../assets/screenshots/demo-read.webp){ .screenshot loading=lazy }

*Captured in VNote 4.9.1 on Windows, using the English interface and the repository's demo notes.*

## 1. Create a notebook

VNote organizes notes into **notebooks**. A notebook is simply a directory on your disk, so the first step is to choose where your notes will live.

1. Open VNote. On the left, open the notebook selector and choose **New Notebook**.
2. Pick an **empty** directory as the *Notebook Root Folder*. With the default **Bundled notebook** type, everything in this notebook — notes, images, and configuration — is stored here.
3. Give the notebook a name and, optionally, a description, then confirm.

!!! tip "Already have Markdown files?"
    Create the notebook as usual, then use **Import Folder** from the toolbar's **New** menu to bring your existing directory in. If you would rather adopt that folder exactly as it is, set the notebook **Type** to **Raw notebook** to browse it in place — at the cost of tags, attachments, and the recycle bin. See [Importing & Migrating](../managing-notes/importing-migrating.md).

## 2. Create a folder (optional)

Notebooks can contain **folders**, nested to any depth. Right-click the notebook in the navigation panel and choose **New Folder** to group related notes. You can skip this and add folders later.

## 3. Create your first note

1. Select the notebook or folder where the note should live.
2. Click **New Note** (or press the shortcut shown in the menu).
3. Enter a name, such as `welcome.md`. The `.md` suffix creates a Markdown note.
4. The note opens in the editor, ready for you to type.

## 4. Write and preview

VNote gives Markdown a **live experience**: as you type, headings, lists, and emphasis are highlighted in place. You can also open a **side-by-side preview** or switch to **read mode** to see the fully rendered result. See [Editor Basics](../editing/editor-basics.md) for the editing modes and the outline.

## 5. Find your notes on disk

Open the Notebook Root Folder in your file manager. The ordinary note you just created is a plain `.md` file. Images inserted as files are stored separately (by default under `vx_assets`); Base64 images are embedded in the note. Back up the complete notebook or configure [Notebook Sync](../managing-notes/notebook-sync.md). If you later enable [note-body encryption](../managing-notes/encrypted-notes.md), preserve its key files and password too: separate assets and earlier backups or Git history are not encrypted by that conversion.

## Next steps

- Learn the [Dashboard](dashboard.md) and main interface.
- Organize with [Notebooks, Folders & Notes](../managing-notes/notebooks-folders-notes.md) and [Tags](../managing-notes/tags.md).
- Explore the [Editing](../editing/index.md) features, from math and diagrams to snippets and templates.

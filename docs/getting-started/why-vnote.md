# Why VNote

VNote is a free and open source, Qt-based note-taking application that focuses on Markdown. It is more than an editor: it pairs a pleasant editing experience with powerful notes management, and runs natively on **Linux**, **Windows**, and **macOS**.

This page explains what makes VNote different and who it is for. If you just want to start taking notes, jump to [Installation](installation.md) and the [Quick Start](quick-start.md).

## What VNote is

VNote organizes your writing into **notebooks**. A notebook is a directory on your disk containing your notes and supporting files. Ordinary Markdown and text notes are plain text; optional [encrypted notes](../managing-notes/encrypted-notes.md) protect their bodies in a format that VNote unlocks with your password.

You stay in control of your local files: back them up, version them, or move the complete notebook to another computer. Ordinary Markdown and text notes can also be edited with other tools. For encrypted notes, preserve the notebook metadata and key files as well as your password; encryption does not erase plaintext from earlier backups or Git history.

## Why choose VNote

<div class="grid cards" markdown>

-   :material-lock-outline:{ .lg .middle } __Own your data__

    ---

    Notes are local files, with optional note-body encryption. One notebook is one directory. Choose folder synchronization or built-in Git, WebDAV, or Jianguoyun sync.

-   :material-folder-multiple-outline:{ .lg .middle } __Simple notes management__

    ---

    Self-contained notebooks, infinite levels of folders, and plain notes. Organize with tags, quick access, and history; explore and edit external files directly.

-   :material-language-markdown:{ .lg .middle } __Pleasant Markdown experience__

    ---

    In-place and side-by-side live preview, syntax highlighting, an interactive outline, effective image management, math, and diagrams (PlantUML, Graphviz, Mermaid, and more).

-   :material-tune:{ .lg .middle } __Made for power users__

    ---

    Vi mode, versatile shortcuts, tabs and window splits, fuzzy search and jump, plus deep customization through themes, styles, and behaviors.

</div>

## Own your data

Privacy and longevity are the heart of VNote's design.

- **Local files.** Ordinary Markdown and text notes remain readable without VNote; [encryption](../managing-notes/encrypted-notes.md) is an opt-in exception for their bodies.
- **One notebook, one directory.** Back up the complete notebook, including its metadata and encryption keys, rather than just the note files.
- **Sync your way.** Use a folder-sync tool or built-in Git, WebDAV (including Nextcloud), or Jianguoyun synchronization. See [Notebook Sync](../managing-notes/notebook-sync.md) for setup and provider differences.
- **Control your data.** Keep ordinary notes in standard formats; decrypt protected notes in VNote before editing their contents with another application.

## Simple, scalable notes management

VNote scales from a handful of notes to large, deeply nested knowledge bases.

- Self-contained notebooks with **infinite levels of folders**.
- [Tags](../managing-notes/tags.md) to organize notes across the folder tree.
- [Quick access and history](../managing-notes/quick-access-history.md) to return to what you were working on.
- Import and migrate existing notes — see [Importing & Migrating](../managing-notes/importing-migrating.md).

## A pleasant Markdown experience

Writing is where VNote spends most of its effort.

- Live preview, both **in-place** and **side-by-side**.
- Syntax highlighting and an interactive [outline](../editing/editor-basics.md).
- Effective [image management](../editing/images-and-image-host.md), including image hosts.
- [Math and diagrams](../editing/math-and-diagrams.md) with PlantUML, Graphviz, Mermaid, and more.
- [Snippets](../editing/snippets.md), [templates](../editing/templates.md), and [mind maps](../editing/mind-maps.md) for structured writing.

## Built for power users

- [Vi mode](../editing/vi-mode.md) for modal editing.
- Tabs, window splits, and versatile [keyboard shortcuts](../customization/keyboard-shortcuts.md).
- Fast [search](../search/index.md) and jump across notebooks.
- Deep [customization](../customization/index.md) of themes, styles, and behaviors.

## Who VNote is for

VNote is a good fit if you:

- Want your notes to be **plain files you own**, not entries in someone else's cloud database.
- Take a lot of **Markdown** notes and care about the editing experience.
- Keep a **large or long-lived** knowledge base and need folders, tags, and search that scale.
- Prefer to **choose your own sync** (folder sync, Git, WebDAV, or Jianguoyun) rather than a VNote-hosted account.
- Enjoy **keyboard-driven, customizable** tools — especially if you like Vi.

You may prefer another tool if you need real-time multi-user collaboration or a fully managed, account-based cloud service — VNote focuses on local-first, single-user note-taking.

## Next steps

- [Install VNote](installation.md) on your platform.
- Follow the [Quick Start](quick-start.md) to create your first notebook.
- Get to know the [Dashboard](dashboard.md).

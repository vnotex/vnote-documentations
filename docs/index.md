# VNote

**A pleasant note-taking platform.**

VNote is a free, open-source note-taking app that makes writing, organizing, and exploring your notes simple and enjoyable.

[Get Started](getting-started/index.md){ .md-button .md-button--primary }
[Download VNote](https://github.com/vnotex/vnote/releases/latest){ .md-button }
[Download VNote from Gitee](https://gitee.com/vnotex/vnote/releases){ .md-button }

![The VNote main window](assets/screenshots/main.webp){ .screenshot }

!!! info "Documentation for VNote 4.14.4"
    Updated for the latest stable release, [VNote 4.14.4](https://github.com/vnotex/vnote/releases/tag/v4.14.4), and recent stable versions since 4.12.0. Before upgrading, check the [platform requirements](getting-started/installation.md#requirements), [notebook task trust](productivity/tasks.md), and [encrypted-note format changes](managing-notes/encrypted-notes.md). Continuous builds may differ from this guide.

## Recent releases

| Stable release | Highlights and guides |
| --- | --- |
| [4.14.4](https://github.com/vnotex/vnote/releases/tag/v4.14.4) · 2026-11-12 | Four [Markers Concealment presets](editing/editor-basics.md#markers-concealment), three Markdown editing experiences, `Ctrl+G, F` for [outline mind maps](editing/mind-maps.md#outline-mind-maps), and direct [Quick Note](productivity/quick-note.md) creation when only one scheme is available. |
| [4.14.2](https://github.com/vnotex/vnote/releases/tag/v4.14.2) · 2026-11-10 | Local trust for [notebook tasks](productivity/tasks.md), Windows [Read/Edit context menus](managing-notes/file-types.md), authenticated [delta updates](getting-started/installation.md#explicit-windows-updates), and [Attach to Main Window](editing/editor-basics.md#detached-windows). |
| [4.14.1](https://github.com/vnotex/vnote/releases/tag/v4.14.1) · 2026-11-08 | Edit Markdown and safely mapped Typst headings through [outline mind maps](editing/mind-maps.md#outline-mind-maps), with source-linked saving and Undo/Redo. |
| [4.14.0](https://github.com/vnotex/vnote/releases/tag/v4.14.0) · 2026-11-05 | Opt-in, notebook-scoped [HTTP API](productivity/http-api.md), formula-preserving [HTML-to-Markdown paste](editing/editor-basics.md#rich-text-and-html-paste), and [United Entry](search/united-entry.md) filename search with explicit `>` commands. |
| [4.13.0](https://github.com/vnotex/vnote/releases/tag/v4.13.0) · 2026-11-02 | Source-bound outline and node-note previews, native [Typst HTML/PDF export](editing/typst.md#pdf-output-and-printing), [source-aware exports](productivity/export.md), and shared [export styling](customization/themes-and-styles.md#applying-export-styles). |

The 4.14.3 release was aborted; its changes are included in 4.14.4. The guides describe the final 4.14.4 behavior, not superseded intermediate settings. Screenshot captions identify older captures where applicable.

## What is VNote?

Whether you're keeping a personal journal, building a knowledge base, taking study notes, writing documentation, or organizing ideas, VNote gives you a comfortable place to keep your work together.

VNote is especially well suited to **Markdown**, combining a powerful editor with practical note-management features. But it goes beyond Markdown: you can also work with **mind maps**, **Typst documents**, **plain text files**, and more, all within the same app.

## Why VNote

<div class="grid cards" markdown>

-   :material-pencil-outline:{ .lg .middle } __Write comfortably__

    ---

    A comfortable editing experience helps you concentrate on your content, whether you're jotting down a thought or writing something longer.

-   :material-folder-multiple-outline:{ .lg .middle } __Keep your notes organized__

    ---

    Organize notes into notebooks and folders, and quickly find what you need as your collection grows.

-   :material-language-markdown:{ .lg .middle } __Use Markdown without the friction__

    ---

    Write and preview Markdown naturally, whether you're new to Markdown or already use it every day.

-   :material-sitemap:{ .lg .middle } __Turn ideas into mind maps__

    ---

    Create and edit mind maps to explore connections and give your ideas a clear visual structure.

-   :material-file-document-outline:{ .lg .middle } __Work with more than notes__

    ---

    Edit plain-text files, write Typst documents with live PDF preview, and read PDFs without switching between apps.

-   :material-lock-outline:{ .lg .middle } __Keep your files in your hands__

    ---

    Keep your work in local files, with notebooks you can back up, move, and manage using familiar tools.

</div>

## Your notes, your way

VNote gives you a flexible workspace built around local files, with support for open formats such as Markdown, plain text, and Typst. Your notes stay under your control.

Start with a few Markdown notes, build a personal knowledge base, sketch an idea as a mind map, or simply use VNote as a pleasant place to write.

**VNote is a home for your notes, ideas, and knowledge.**

## Explore the documentation

<div class="grid cards" markdown>

-   :material-rocket-launch-outline:{ .lg .middle } __Getting Started__

    ---

    Install VNote, take your first note, and get to know the dashboard.

    [:octicons-arrow-right-24: Getting Started](getting-started/index.md)

-   :material-notebook-outline:{ .lg .middle } __Managing Notes__

    ---

    Organize notebooks, folders, and notes; use tags, sync, quick access, and history.

    [:octicons-arrow-right-24: Managing Notes](managing-notes/index.md)

-   :material-pencil-outline:{ .lg .middle } __Editing__

    ---

    Write and format across VNote's editors — Markdown, Typst, math, diagrams, snippets, templates, mind maps, and Vi mode.

    [:octicons-arrow-right-24: Editing](editing/index.md)

-   :material-magnify:{ .lg .middle } __Search__

    ---

    Find notes fast with the search panel and the united entry.

    [:octicons-arrow-right-24: Search](search/index.md)

-   :material-lightning-bolt-outline:{ .lg .middle } __Productivity__

    ---

    Automate work with tasks and export your notes to other formats.

    [:octicons-arrow-right-24: Productivity](productivity/index.md)

-   :material-cog-outline:{ .lg .middle } __Customization__

    ---

    Configure settings, apply themes and styles, and tailor keyboard shortcuts.

    [:octicons-arrow-right-24: Customization](customization/index.md)

</div>

## Open source and free

- Licensed under [GNU LGPLv3](https://opensource.org/licenses/LGPL-3.0).
- Powered by Qt and C++.
- Available on Linux, Windows, and macOS.

## Get involved

- Star and follow VNote on [GitHub](https://github.com/vnotex/vnote).
- Report issues via [GitHub Issues](https://github.com/vnotex/vnote/issues).

!!! tip "Need help?"
    Check the [Help](help/index.md) section for frequently asked questions and data migration guidance.

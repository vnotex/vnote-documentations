# Editor Basics

VNote's editor is where you spend most of your time, so it is built to make Markdown feel natural: you keep track of your content while you write, and see a beautiful rendering when you read. This page covers the editing modes, the outline, tabs and splits, and the everyday actions that make up a writing session.

Tabs, splits, the outline, and note navigation apply to every editor, but features such as edit/read mode, live preview, and Cross Copy or Parse to Markdown are specific to the Markdown editor.

## Edit mode and read mode

Every note opens in one of two modes:

- **Edit mode** shows your Markdown source with rich **syntax highlighting**. Headings, emphasis, links, code, and other elements are styled in place, so the text stays readable without a separate preview. This is VNote's answer to the usual "edit vs. preview" split — see [Why VNote](../getting-started/why-vnote.md).
- **Read mode** renders the note to its final, formatted form for comfortable reading and sharing.

Toggle between the two from the editor toolbar or with the mode shortcut. Read mode is also what export is based on — see [Export](../productivity/export.md).

![Edit mode: Markdown source with syntax highlighting](../assets/screenshots/md-edit.webp){ .screenshot loading=lazy }

![Read mode: the same note rendered](../assets/screenshots/md-read.webp){ .screenshot loading=lazy }

## Live preview

While in edit mode, VNote can preview rich elements without sending you to read mode:

- **In-place preview** renders elements such as images, math, diagrams, and tables directly inside the editor, right where they appear in the text. In-place previews zoom together with the editor, and the source block is folded automatically when its preview appears — if you unfold it by hand, VNote leaves it unfolded.
- **Side-by-side preview** opens a rendered pane next to the editor that scrolls in sync as you type, when you prefer to see the full result while writing.

Use whichever fits the note; you can turn side-by-side preview on and off at any time.

The **interactive table preview** is enabled by default: a Markdown table is previewed as a real editable sheet with syntax-highlighted cells, row, column and alignment operations from its **Table** menu, and `Enter` in the last cell appending a row. Edits go straight back into the Markdown source.

Two options under **Settings → Markdown Editor** control how that write-back looks and how previews affect the source. **Align table source** formats a table edited through the preview as a column-aligned pipe table; it never reformats existing tables until you edit them. **Auto fold previewed blocks** folds a block's source when its in-place preview appears; it requires text folding, and turning it off does not unfold blocks already folded.

Large notes render previews incrementally. Off-screen tables keep their layout space and are built only when needed, visible graph previews take priority, and read-mode diagrams appear progressively. Table cell syntax highlighting is capped at 5000 cells in extreme documents; the remaining cells and table content still render.

## The outline

The **Outline** dock widget shows the heading structure of the current note. It updates as you write and is fully interactive — click any heading to jump straight to that section. In edit mode it shows rendered heading titles rather than raw Markdown, and the pane scrolls horizontally when a label is too long to fit. For long notes, the outline is the fastest way to move around and to sanity-check your document's structure.

## Detached windows

A view does not have to stay inside the main window:

- **Detach** in the tab context menu (`Ctrl+G, Shift+D`) moves the current tab into its own top-level window.
- **Open as Detached** in the notebook explorer context menu opens a note directly in a detached window.
- The `--detached-view` [command line](../getting-started/command-line.md) option does the same from a terminal or a script.

A detached window carries a **Stay on Top** pin (`F10`) so you can keep it above other windows while you work elsewhere — useful for a reference note or a [PDF](../managing-notes/pdf-viewer.md).

## The Home tab

VNote starts on the [Dashboard](../getting-started/dashboard.md) Home tab. Opening a file in the main area closes it when it is the only tab there, so you are not left with a stale placeholder; opening a file in a detached window leaves it alone. Home comes back as soon as the main area is empty again. There is no setting to configure.

## Reloading

A note can change on disk — a sync, another editor, a script. VNote detects the change and reloads the buffer, and your caret position is restored afterwards. The same applies to an explicit reload, to changing a note's encoding, and to the resynchronization that happens when the window regains focus.

## Tabs, splits, and navigation

- **Tabs** — notes open as tabs in the content area, so you can keep several open and switch between them.
- **Splits** — divide the content area into side-by-side views to compare two notes, or to reference one while editing another.
- **Jump around** — use the outline, [Search](../search/index.md), [United Entry](../search/united-entry.md), and [History](../managing-notes/quick-access-history.md) to move quickly, especially in large notebooks.

![The content area split into side-by-side views](../assets/screenshots/splits.webp){ .screenshot loading=lazy }

## Copying and pasting

Beyond plain copy and paste, the Markdown editor has several helpers for moving content in and out of VNote:

- **Insert From Clipboard** — paste a URL and VNote asks how you want it inserted instead of dropping in the bare text. **Insert As Link** wraps it in a Markdown link and **Insert As Text** pastes it verbatim; further choices appear when the URL points at an image, at a local file, or at a file you can attach to the note.
- **Cross Copy** — in **read mode**, select the rendered content and use **Cross Copy** from the context menu to copy it as rich text tuned for a specific target application. VNote rewrites the underlying HTML per target — options include **No Background**, **Evernote**, **OneNote**, **Microsoft Word**, **WeChat Public Account Editor**, and **Raw HTML** — so the formatting survives when you paste into that app.
- **Parse to Markdown and Paste** — when the clipboard contains HTML (for example content copied from a web page), use **Parse to Markdown and Paste** from the editor's context menu (default `Ctrl+G, Ctrl+P`) to convert that HTML to Markdown and insert it. If **Fetch images to local in Parse To Markdown And Paste** is enabled in [Settings](../customization/settings.md), remote images in the pasted content are downloaded into the note's assets and their links rewritten.

![The Insert From Clipboard popup, offering Insert As Link or Insert As Text](../assets/screenshots/link-insert.webp){ .screenshot loading=lazy }

## Everyday editing

The editor supports the usual essentials — undo/redo, find and replace within a note, and copy/paste — plus VNote-specific accelerators you will meet in the following pages:

- [Markdown Syntax](markdown-syntax.md) for the formatting VNote understands.
- [Images & Image Host](images-and-image-host.md) for pasting and managing images.
- [Math & Diagrams](math-and-diagrams.md) for formulas and diagrams.
- [Snippets](snippets.md) and [Templates](templates.md) to avoid repetitive typing.
- [Vi Mode](vi-mode.md) for modal, keyboard-driven editing.

Almost every action has a keyboard shortcut; see [Keyboard Shortcuts](../customization/keyboard-shortcuts.md) to work without reaching for the mouse.

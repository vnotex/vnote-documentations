# Editor Basics

VNote's editor is where you spend most of your time, so it is built to make Markdown feel natural: you keep track of your content while you write, and see a beautiful rendering when you read. This page covers the editing modes, the outline, tabs and splits, and the everyday actions that make up a writing session.

Tabs, splits, the outline, and note navigation apply to every editor, but features such as edit/read mode, live preview, and Cross Copy or Parse to Markdown are specific to the Markdown editor.

## Edit mode and read mode

Every note opens in one of two modes:

- **Edit mode** shows your Markdown source with rich **syntax highlighting**. Headings, emphasis, links, code, and other elements are styled in place, so the text stays readable without a separate preview. This is VNote's answer to the usual "edit vs. preview" split — see [Why VNote](../getting-started/why-vnote.md).
- **Read mode** renders the note to its final, formatted form for comfortable reading and sharing.

Toggle between the two from the editor toolbar or with the mode shortcut. Read mode is also what export is based on — see [Export](../productivity/export.md).

## Live preview

While in edit mode, VNote can preview rich elements without sending you to read mode:

- **In-place preview** renders elements such as images, math, and diagrams directly inside the editor, right where they appear in the text.
- **Side-by-side preview** opens a rendered pane next to the editor that scrolls in sync as you type, when you prefer to see the full result while writing.

Use whichever fits the note; you can turn side-by-side preview on and off at any time.

## The outline

The **Outline** dock widget shows the heading structure of the current note. It updates as you write and is fully interactive — click any heading to jump straight to that section. For long notes, the outline is the fastest way to move around and to sanity-check your document's structure.

## Tabs, splits, and navigation

- **Tabs** — notes open as tabs in the content area, so you can keep several open and switch between them.
- **Splits** — divide the content area into side-by-side views to compare two notes, or to reference one while editing another.
- **Jump around** — use the outline, [Search](../search/index.md), [United Entry](../search/united-entry.md), and [History](../managing-notes/quick-access-history.md) to move quickly, especially in large notebooks.

## Copying and pasting

Beyond plain copy and paste, the Markdown editor has two helpers for moving formatted content in and out of VNote:

- **Cross Copy** — in **read mode**, select the rendered content and use **Cross Copy** from the context menu to copy it as rich text tuned for a specific target application. VNote rewrites the underlying HTML per target — options include **No Background**, **Evernote**, **OneNote**, **Microsoft Word**, **WeChat Public Account Editor**, and **Raw HTML** — so the formatting survives when you paste into that app.
- **Parse to Markdown and Paste** — when the clipboard contains HTML (for example content copied from a web page), use **Parse to Markdown and Paste** from the editor's context menu (default `Ctrl+G, Ctrl+P`) to convert that HTML to Markdown and insert it. If **Fetch images to local in Parse To Markdown And Paste** is enabled in [Settings](../customization/settings.md), remote images in the pasted content are downloaded into the note's assets and their links rewritten.

## Everyday editing

The editor supports the usual essentials — undo/redo, find and replace within a note, and copy/paste — plus VNote-specific accelerators you will meet in the following pages:

- [Markdown Syntax](markdown-syntax.md) for the formatting VNote understands.
- [Images & Image Host](images-and-image-host.md) for pasting and managing images.
- [Math & Diagrams](math-and-diagrams.md) for formulas and diagrams.
- [Snippets](snippets.md) and [Templates](templates.md) to avoid repetitive typing.
- [Vi Mode](vi-mode.md) for modal, keyboard-driven editing.

Almost every action has a keyboard shortcut; see [Keyboard Shortcuts](../customization/keyboard-shortcuts.md) to work without reaching for the mouse.

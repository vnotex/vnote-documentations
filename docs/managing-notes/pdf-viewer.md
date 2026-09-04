# PDF Viewer

VNote opens `.pdf` files in a built-in viewer based on pdf.js 6.2.108, so a PDF that lives in a notebook — a paper, a manual, a scanned handout — can be read and annotated next to your notes without leaving the application. The PDF file itself remains read-only: comments are saved separately, and you cannot create a PDF note (see [File Types](file-types.md)).

![A PDF opened in VNote's built-in viewer](../assets/screenshots/pdf.webp){ .screenshot loading=lazy }

## Reading a PDF

Open a PDF the way you open any other note — from the notebook explorer, from [Quick Access & History](quick-access-history.md), or by dragging the file into the content area. Native toolbar controls provide page navigation, zoom, rotation, text selection, hand scrolling, scroll and spread modes, document properties, presentation mode, and text search; less common controls are grouped under **More**.

Because a PDF opens in an ordinary view window, everything you know about tabs applies: you can split the content area and keep the PDF beside the note you are writing, or detach it into its own window. See [Editor Basics](../editing/editor-basics.md).

The viewer's navigation pane contains thumbnails, bookmarks, attachments, and layers. It is hidden when a document opens so the page gets the full width; use **Toggle Sidebar** in the toolbar when you need it.

## Outline and bookmarks

If the PDF carries an embedded outline (its bookmarks), VNote reads it and offers two ways to navigate:

- The **Outline** dock shows the PDF's outline just like the heading structure of a Markdown note. Click an entry to jump to that page.
- Each view window has an **Outline** popup in its toolbar, which is handy for a detached or split window that cannot see the dock.

Very large outlines are truncated at 5000 entries; the rest of the document is still fully readable.

## Comments and annotations

The PDF toolbar has three annotation tools. Click a tool's main button to arm or disarm it; use the dropdown on that same button to configure it:

- **Highlight** — drag across text to highlight it, or select text first and choose **Highlight** from the page context menu. Its menu sets the color.
- **Draw** — drag on the page to add freehand ink. Its menu sets the color, line thickness, and opacity.
- **Text box** — click to place a box and type directly in it. Press `Ctrl+Enter` or click away to finish, double-click an existing box to edit it, and drag a box to move it. Its menu sets the color and font size.

Open the **Comments** dock to browse annotations by page. Selecting an item jumps to it; the lower pane lets you add or edit its note, change its color, or delete it. Annotation changes are saved automatically and never mark the PDF itself as modified.

Comments are stored per file. A bundled notebook keeps `comments.json` in that file's attachment folder, so it travels with the notebook and participates in built-in sync. A raw notebook or external PDF uses a sibling `<filename>.pdf.comments.json` file. VNote carries the sidecar along when it renames, moves, or deletes the PDF.

## Limitations

The PDF itself remains read-only; filling forms and changing document content still require a dedicated PDF application. To turn your own notes into a PDF, see [Export](../productivity/export.md).

!!! warning "The built-in viewer requires Qt 6.9 or newer"
    Current regular Windows, Linux, and macOS packages meet this requirement. The `win64-windows7` package uses Qt 5.15, so VNote does not create a built-in PDF tab there; it opens the configured external PDF application, or the system default when none is configured. You can choose one under **Settings → File Associations → External Programs**.

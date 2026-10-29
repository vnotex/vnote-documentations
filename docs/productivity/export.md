# Export

VNote exports Markdown notes and mind maps to shareable formats: **Markdown**, **HTML**, and **PDF** out of the box, plus other formats through **Pandoc** or a custom command. Native `.typst` notes have a separate [PDF output workflow](../editing/typst.md#pdf-output-and-printing); the general Export dialog does not save their compiled preview.

## Starting an export

Open the export dialog from the main file toolbar, from the Markdown **read-mode context menu → Export**, or with `Ctrl+G, T`. Right-click the background of a mind map to find **Export** there too. In Markdown read mode, right-click plain document content rather than a link or image to see Export. A file opened from outside any notebook can be exported too.

[Encrypted note bodies](../managing-notes/encrypted-notes.md) cannot be exported or printed, even while unlocked. If an export selection contains encrypted notes, VNote refuses the export rather than exporting a partial selection.

## General settings

In the export dialog you choose the scope and the target:

- **Scope** — **Current buffer** uses the open editor's live content, including unsaved changes; **Current note**, folder, and notebook exports use saved files on disk. Save first if you want those scopes to include your latest edits. The notebook scope shows the notebook name.
- **Target format** — `Markdown`, `HTML`, `PDF`, or `Custom`.
- **Rendering style / Syntax style** — choose styles for the exported page and code highlighting, independently of the editor (styles come from your [theme](../customization/themes-and-styles.md)). The first opening of the dialog in each session selects the active theme's styles; later choices are retained. Click the compact palette-icon **Follow Theme** button to select the current theme again.

## Markdown

Exports the note as a `Markdown` file into a single folder, together with its images and attachments. Useful for producing a clean, self-contained copy.

## HTML

Exports the note to a single `HTML` page that opens anywhere in a browser. **Complete page (pack all resources)** copies the resources the page references next to the exported file — or embeds them when **Embed images** is also checked — so the page renders standalone.

HTML uses the selected theme’s palette, including table borders and other themed colors. **Add outline panel** supplies a collapsible outline with active-section highlighting and keyboard-accessible controls. Code blocks retain **Copy** and **Collapse/Expand** controls; copying a collapsed block copies all its code. [Heading folding](../editing/editor-basics.md) also applies to HTML export when enabled.

Following a relative `.md` link in an exported page offers the corresponding `.html` target, preserving any query string or heading fragment. Accept to follow the HTML version, or decline to keep the original Markdown target. This choice does not create or check the target file: export the linked notes and keep their relative layout yourself.

## PDF

Exports to `PDF` either directly or via the `wkhtmltopdf` tool. **Use wkhtmltopdf (outline supported)** adds support for a document **outline** (bookmarks); the fields that only apply to it, **Wkhtmltopdf path** and **Wkhtmltopdf arguments**, are greyed out while the option is off.

CJK text and Mermaid labels render correctly in `wkhtmltopdf` output; if no CJK-capable font can be loaded, the dialog warns you instead of quietly producing boxes. Mermaid diagrams are rasterized at their printed size and 384 dpi, so they stay sharp in print.

If the `wkhtmltopdf` process fails, the failure is reported in the dialog's log pane rather than producing nothing without explanation.

The **All-In-One** option combines multiple source notes into a single target file — handy for turning a folder of notes into one document.

## Mind-map exports

Mind maps support **Markdown**, **HTML**, and **PDF**, including independent trees:

- **Markdown** produces a readable document from the topics and their content, rather than a picture of the canvas. Peer roots remain at the same heading level.
- **HTML** includes a full-width map at its natural size, with selectable topic text and SVG connectors. Topic links lead to continuous articles containing node notes, images, icons, tags, and links.
- **PDF** fits the map onto the first page, then places the node articles on subsequent pages for reading. This differs from printing the canvas alone.

Use **Current buffer** to include live edits; **Current note** and batch exports read the saved map. The exporter waits for images and fonts before PDF output and reports rendering or output failures in the log pane.

## Printing

For Markdown, **Print** uses the rendered document in read mode and the current source in edit mode, including selections and live-preview split layouts. Switch to read mode first when you want a formatted document rather than source text.

For a mind map, choose **Print** from the editor toolbar's three-dot **Menu**. It fits the current canvas layout onto one page, including vector text, images, links, and any active inline draft. Use PDF export instead when you also want the node articles.

## Custom

The **Custom** target runs a command of your choice, most often [Pandoc](https://pandoc.org/), to reach formats such as `docx`, `epub`, and many more. Refer to Pandoc's documentation for the details, or plug in your own script.

For example, on Windows this command exports to nearly any format via Pandoc — just change the **target file suffix** to `docx`, `epub`, and so on:

```
"c:\your\path\to\pandoc.exe" --resource-path=.;%2 --css=%3 --css=%4 -s -o %5 %1
```

On non-Windows platforms, change the path separator from `;` to `:`.

## Tips

- Markdown HTML/PDF export uses **read-mode** rendering. Check math, diagrams, and images there first — see [Editor Basics](../editing/editor-basics.md). Typst math and fenced `typst` blocks embedded in Markdown are supported; this is different from exporting a native `.typst` note.
- For `PDF` with a clickable outline, install `wkhtmltopdf` and select it in the dialog.
- For repeatable, scriptable conversions, a [Task](tasks.md) that calls Pandoc can complement the export dialog.

# Export

VNote exports your notes to shareable formats: **Markdown**, **HTML**, and **PDF** out of the box, plus almost anything else through **Pandoc** or a custom command.

## Starting an export

Open the export dialog from the toolbar, from the Markdown **read-mode context menu → Export**, or with `Ctrl+G, T`. A file opened from outside any notebook can be exported too, not just notes that belong to a notebook.

## General settings

In the export dialog you choose the scope and the target:

- **Scope** — export the current note, all notes in the current folder, or all notes in the current notebook.
- **Target format** — `Markdown`, `HTML`, `PDF`, or `Custom`.
- **Rendering style** — you can apply a different style for the exported output than the one you edit with (styles come from your [theme](../customization/themes-and-styles.md)). The dialog remembers the theme you used last.

## Markdown

Exports the note as a `Markdown` file into a single folder, together with its images and attachments. Useful for producing a clean, self-contained copy.

## HTML

Exports the note to a single `HTML` page that opens anywhere in a browser. **Complete page (pack all resources)** copies the resources the page references next to the exported file — or embeds them when **Embed images** is also checked — so the page renders standalone.

## PDF

Exports to `PDF` either directly or via the `wkhtmltopdf` tool. **Use wkhtmltopdf (outline supported)** adds support for a document **outline** (bookmarks); the fields that only apply to it, **Wkhtmltopdf path** and **Wkhtmltopdf arguments**, are greyed out while the option is off.

CJK text and Mermaid labels render correctly in `wkhtmltopdf` output; if no CJK-capable font can be loaded, the dialog warns you instead of quietly producing boxes. Mermaid diagrams are rasterized at their printed size and 384 dpi, so they stay sharp in print.

If the `wkhtmltopdf` process fails, the failure is reported in the dialog's log pane rather than producing nothing without explanation.

The **All-In-One** option combines multiple source notes into a single target file — handy for turning a folder of notes into one document.

## Custom

The **Custom** target runs a command of your choice, most often [Pandoc](https://pandoc.org/), to reach formats such as `docx`, `epub`, and many more. Refer to Pandoc's documentation for the details, or plug in your own script.

For example, on Windows this command exports to nearly any format via Pandoc — just change the **target file suffix** to `docx`, `epub`, and so on:

```
"c:\your\path\to\pandoc.exe" --resource-path=.;%2 --css=%3 --css=%4 -s -o %5 %1
```

On non-Windows platforms, change the path separator from `;` to `:`.

## Tips

- Export is based on **read mode** rendering, so what you see in read mode is what you get. Check math, diagrams, and images render correctly there first — see [Editor Basics](../editing/editor-basics.md).
- For `PDF` with a clickable outline, install `wkhtmltopdf` and select it in the dialog.
- For repeatable, scriptable conversions, a [Task](tasks.md) that calls Pandoc can complement the export dialog.

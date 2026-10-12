# File Types

A VNote note is just a file on disk, and VNote recognizes a handful of built-in file types by their extension. The type decides which editor or viewer opens the file, and whether you can create a new note of that type.

## Supported types

| Type | Extensions | Opens in | Create as a new note? |
|------|------------|----------|-----------------------|
| **Markdown** | `.md`, `.mkd`, `.rmd`, `.markdown` | Markdown editor | Yes |
| **Text** | `.txt`, `.text`, `.log`, many source and configuration suffixes, and any other file detected as plain text | Text editor | Yes |
| **Mind Map** | `.mmm` (preferred), `.emind` | Native mind-map editor | Yes |
| **PDF** | `.pdf` | [Built-in PDF viewer](pdf-viewer.md) | No — view only |
| **Others** | anything else | Text editor | Yes — no extension is added |

Markdown is the core note type and gets VNote's full editing experience — see [Editing](../editing/index.md). Text and source files open in the [text editor](../editing/text.md), and mind maps are a distinct visual note type covered in [Mind Maps](../editing/mind-maps.md).

![A PDF opened in VNote's built-in viewer](../assets/screenshots/pdf.webp){ .screenshot loading=lazy }

## How the type is chosen

For ordinary, unencrypted files, VNote matches the extension against the table above. A file whose extension is not listed but whose contents are plain text is treated as a **Text** file, so you can open and edit it directly. Anything left over falls under **Others**, which also opens in the [text editor](../editing/text.md) — VNote does not hand it to another application on its own.

To open a given extension somewhere else, add an entry under **Settings → File Associations → External Programs**. You can point a suffix at a specific command or at your system's default application, and from then on VNote hands those files over instead of opening them itself. The same settings page is where you edit the suffix list of each built-in type; existing custom mind-map suffixes are retained.

### Encrypted-note exception

Bundled notebooks can protect the bodies of Markdown, text, and mind-map notes. These are not ordinary plaintext files for external programs: VNote unlocks them and uses their protected note type to choose the editor. Do not rename an encrypted file's extension to convert it or expect an external editor to read it. See [Encrypted Notes](encrypted-notes.md) for supported operations and protection limits.

## Creating notes

When you choose **New Note**, the **Type** dropdown lets you create a **Markdown**, **Text**, **Mind Map**, or **Others** note — **Others** creates a file without adding any extension. PDF is the one type you cannot create: it is view-only, so you can open and read a `.pdf` that lives in a notebook, but you cannot create a new PDF note from within VNote. (VNote can still *export* your notes to PDF — see [Export](../productivity/export.md).)

Because everything is just files, you can also drop files of any of these types into a notebook folder on disk, and VNote will open each one with the matching editor or viewer.

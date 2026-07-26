# Themes & Styles

A **theme** controls how VNote looks — the interface, the editor and read mode, and the syntax highlighting of code blocks. VNote ships with several themes, and because a theme is just a folder of files, you can copy one and tweak it to make VNote your own.

## Themes

A theme corresponds to a folder inside the `themes` folder. Choose and manage themes in the **Settings** dialog. See [Settings](settings.md) for where the configuration and theme folders live.

### Add a theme

The easiest way to start is from an existing theme:

1. Copy the folder of a theme you like.
2. Paste it into the `themes` folder under your **user configuration** folder.
3. Rename the folder — this becomes the theme's name.

Then edit the files inside to taste.

### What's in a theme

Key files of a theme:

- `palette.json` — the theme's palette; defines colors reused throughout the theme.
- `interface.qss` — a [Qt Style Sheet](http://doc.qt.io/qt-5/stylesheet-reference.html) that styles every widget; it uses the colors from `palette.json`.
- `text-editor.theme` — the theme of the text editor (and Markdown editor).
- `web.css` — the style sheet for Markdown **read mode**.
- `highlight.css` — read-mode code-block syntax highlighting (VNote uses [Prism](https://prismjs.com/) in read mode).
- `icons/` — optional folder of custom icons.

## Customizing fonts

### Read mode

Read-mode fonts are set in `web.css`. Body text uses `font-family` and `font-size` on `body`:

```css
body {
    font-family: -apple-system, "Noto Sans", "Segoe UI", sans-serif;
    font-size: 16px;
    line-height: 1.5;
}
```

Code fonts are set on `code` and `pre code`:

```css
code {
    font-family: Consolas, Monaco, Monospace, Courier;
}
```

Syntax-highlighted code blocks are styled in `highlight.css` (the `code[class*="language-"]` / `pre[class*="language-"]` rules).

### Text and Markdown editor

Editor fonts are set in `text-editor.theme`. Set `font-family` and `font-size` under the editor's `Text` style:

```json
{
    "editor-styles": {
        "Text": {
            "font-family": "Consolas, Monaco, Monospace, Courier New",
            "font-size": 12
        }
    }
}
```

There is a parallel `markdown-editor-styles` block for the Markdown editor.

### Interface fonts

To change interface fonts (menus, trees), edit `interface.qss` with Qt Style Sheet rules. The [Qt docs](https://doc.qt.io/qt-5/stylesheet-examples.html) have many examples.

```css
QWidget { font-size: 12pt; }

QTreeView, QListView { font-size: 12pt; }

vnotex--NotebookNodeExplorer QTreeView { font-size: 14pt; }
```

## Customizing icons

Put icon files in a theme's `icons` folder to override VNote's icons. For the full list of icon file names, see the [icons in the VNote source](https://github.com/vnotex/vnote/tree/master/src/data/core/icons).

A typical theme directory:

```
.
├── cover.png
├── highlight.css
├── icons
│   ├── ***.svg
│   └── ***.svg
├── interface.qss
├── palette.json
├── text-editor.theme
└── web.css
```

Some commonly replaced icons:

- **Notes:** `folder_node.svg` (folder), `file_node.svg` (note).
- **Top menu bar:** `notebook_menu.svg`, `new_note.svg`, `import_menu.svg`, `export_menu.svg`, `flash_page_menu.svg`, `quick_access_menu.svg`, `task_menu.svg`, `united_entry.svg`, `expand.svg`, `settings_menu.svg`, `menu.svg`.
- **Left navigation bar:** `navigation_dock.svg`, `history_dock.svg`, `tag_dock.svg`, `search_dock.svg`, `snippet_dock.svg`.

## Applying export styles

Because read mode uses these styles, they also drive [export](../productivity/export.md) — you can select a different rendering style for exported output in the export dialog.

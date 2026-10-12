# Mind Maps

Beyond Markdown, VNote supports **mind maps** as a first-class note type. A mind map is its own kind of note — created, edited, and stored inside a notebook just like a Markdown note — that you build visually as a tree of connected nodes rather than writing as text.

## Mind maps are their own note type

In VNote a mind map is **not** a rendering of a Markdown document; it is a distinct file type opened in the native **m3 mind-map editor**. The preferred built-in extension is now `.mmm`; `.emind` remains supported, and existing custom suffix settings are preserved. Mind maps sit alongside Markdown notes in the same notebook, folder tree, and navigation panel.

Because a mind map is a real note, everything you know about [managing notes](../managing-notes/notebooks-folders-notes.md) applies: it lives inside the Notebook Root Folder, travels with the notebook when you copy or [sync](../managing-notes/notebook-sync.md) it, and can be organized in folders.

## Creating a mind map

Create a mind map the same way you create any note — through **New Note** — and choose the **Mind Map** type instead of Markdown. With the default suffix settings, VNote creates an `.mmm` note. An empty map opens with a **Central topic** ready to edit; add child and sibling nodes to build the map.

## Editing a mind map

The mind-map editor is a visual, node-based canvas: you add child and sibling nodes, connect and rearrange them, and build out branches to structure ideas radially. This makes mind maps well suited to brainstorming, planning, and outlining relationships that are awkward to express as a linear document.

![Native m3 mind-map editor with a branching map and the selected node's properties](../assets/screenshots/mindmap.webp){ .screenshot loading=lazy }

VNote 4.9.1 on Windows with the English interface: the native m3 editor at 85% zoom, with the Tools panel floated as **Node Properties** for the selected **Plan** node. This illustration uses a separate sample map, not the demo notebook.

The native editor includes node formatting, links, images, Find, an outline, and Undo/Redo. Folding a branch changes only the current editor's view, not the saved map or another open view; folding and expanding preserve node positions.

### Node properties and the Tools dock

By default, node properties appear in the **Tools** dock, whose title and contents follow the active view. Edit the selected node's properties there. To keep the properties panel inside the editor instead, turn off **Settings → Editor → Mind Map Editor → Separate node properties panel**, then close and reopen the map. Collapsing the embedded properties panel is a separate operation from showing or hiding the Tools dock through **View → Windows List**.

### Zoom and presentation

Maps open and reload at **100%** zoom. The toolbar offers zoom out/in, **Fit**, and **100%**, **125%**, **150%**, and **200%** presets. To use another scale, type a positive percentage in the zoom field and press `Enter`. The controls also track keyboard zoom commands and `Ctrl+wheel`.

Press `F9` (or **Presentation Mode**) to present the current map fullscreen, and `Escape` to exit. The embedded node-properties panel starts collapsed, and the toolbar fades out of the way; this is view presentation, not the application's `F11` fullscreen toggle.

### Mind-map settings

Under **Settings → Editor → Mind Map Editor**, configure:

- **Font family** and **Font size** — defaults for node text; an empty family uses the interface font, and node-specific sizes still override the default size.
- **Undo limit** — the maximum retained document commands; `0` means unlimited. Lowering the limit discards excess Undo/Redo history.
- **Confirm subtree deletion** — ask before deleting nodes and their descendants.
- **Automatic branch colors** — assign colors to new main branches without recoloring existing nodes.
- **Separate node properties panel** — enabled by default; determines whether properties use the Tools dock as described above.

Apply font and behavior changes to update open maps without reloading them. The separate-panel option is the exception and requires closing and reopening the editor. Mind-map-specific bindings live under `editor.mindMapEditor.shortcuts`; shared view shortcuts such as `PresentationMode` use `editor.core.shortcuts`. See [Settings](../customization/settings.md) and [Keyboard Shortcuts](../customization/keyboard-shortcuts.md).

## Mind maps vs. Markdown outlines

- Reach for a **mind map** when you want a free-form, visual tree of ideas that you manipulate directly.
- Reach for a **Markdown note** with headings and nested lists when you want linear, text-first content; its structure still drives the interactive [outline](editor-basics.md) and can be exported. See [Markdown Syntax](markdown-syntax.md).

The two are complementary note types — pick whichever fits how you want to capture the material.

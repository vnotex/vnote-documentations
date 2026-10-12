# Keyboard Shortcuts

VNote is built to be driven from the keyboard. Almost every action has a shortcut, many actions use **chord shortcuts** (press one combination, then another), and the whole scheme is configurable. Combine this with [Vi mode](../editing/vi-mode.md) and you can work almost entirely without the mouse.

## Chord shortcuts

Some VNote shortcuts are chords, written as two parts separated by a comma. For example:

- `Ctrl+G, S` — open the [snippet](../editing/snippets.md) panel: press `Ctrl+G`, release, then press `S`.
- `Ctrl+G, I` — apply a snippet at the cursor.
- `Ctrl+G, G` — activate [United Entry](../search/united-entry.md).

The `Ctrl+G` prefix leads to a family of "go / global" actions; type the prefix and VNote shows you the follow-up keys.

## Navigation mode

**Navigation mode** lets you reach a widget in a few keystrokes, without the mouse. Press `Ctrl+G, W` and VNote overlays key labels on whatever you can navigate to right now — a whole widget, or the individual items inside one; type the key, or the two-key sequence, shown on the one you want. Any key that does not match cancels the mode, so `Esc` gets you out.

![Navigation mode, with key labels overlaid on the interface](../assets/screenshots/navigation-mode.webp){ .screenshot loading=lazy }

## Default dock and window shortcuts

These application-level actions are the ones you reach for daily. The names are the keys used under `core.shortcuts`, and `Ctrl+G` is the configurable leader key:

| Action | Default | What it does |
|--------|---------|--------------|
| `NavigationDock` | `Ctrl+G, A` | Focus the Notebooks dock. |
| `OutlineDock` | `Ctrl+G, U` | Focus the Outline dock. |
| `SnippetDock` | `Ctrl+G, S` | Focus the Snippets dock. |
| `LocationListDock` | `Ctrl+G, C` | Focus the Location List dock. |
| `SearchDock` | unbound | Focus the Search dock. |
| `HistoryDock` | unbound | Focus the History dock. |
| `TagDock` | unbound | Focus the Tags dock. |
| `ConsoleDock` | unbound | Focus the Console dock. |
| `CloseFocus` | `Ctrl+G, X` | Close the focused dock — or the current tab when the editor has focus. |
| `Detach` | `Ctrl+G, Shift+D` | Detach the current view into its own window. |
| `StayOnTop` | `F10` | Pin a detached window above the others. |
| `Export` | `Ctrl+G, T` | Open the [Export](../productivity/export.md) dialog. |
| `UnitedEntry` | `Ctrl+G, G` | Activate [United Entry](../search/united-entry.md). |

Actions listed as unbound have no default; give them one in `core.shortcuts` as described below.

!!! note "`CloseTab` was renamed"
    The action formerly called `CloseTab` is now `CloseFocus`. A customized `CloseTab` binding in an existing `vnotex.json` is still honored, and is written back as `CloseFocus` the next time the configuration is saved.

## View presentation and global Quick Note

**PresentationMode** defaults to `F9` and belongs to `editor.core.shortcuts`, not the application-level table above. It presents the active [Markdown](../editing/editor-basics.md), [text](../editing/text.md), [mind-map](../editing/mind-maps.md), or [PDF](../managing-notes/pdf-viewer.md) view; `Escape` exits. It is distinct from the main-window `FullScreen` action (`F11`).

**NewQuickNote** uses `core.shortcuts.NewQuickNote` (default `Ctrl+Alt+Q`) and is registered as a global hotkey while VNote is running, subject to operating-system availability and shortcut conflicts. It opens the [Quick Note](../productivity/quick-note.md) scheme picker even when the main window is hidden. The default-on **Allow Ctrl+Alt shortcuts** setting can disable this and other `Ctrl+Alt` bindings after a restart; see [Settings](settings.md#general-settings).

## Where shortcuts are defined

Shortcuts live in the main configuration file `vnotex.json`, in two tables: application-level actions under `core.shortcuts`, and editor/editing actions (Save, bold, headings, Find, apply snippet, and so on) under `editor.core.shortcuts`. Each action maps to a key sequence, for example:

```json
"core": {
    "shortcuts": {
        "UnitedEntry": "Ctrl+G, G",
        "FullScreen": "F11"
    }
},
"editor": {
    "core": {
        "shortcuts": {
            "ApplySnippet": "Ctrl+G, I",
            "PresentationMode": "F9"
        }
    }
}
```

To see the authoritative list of every action and its default binding, inspect the `core.shortcuts` and `editor.core.shortcuts` sections of your `vnotex.json` (the defaults are filled in by VNote). See [Settings](settings.md) for where these folders are and how the default/user layers work.

## Customizing a shortcut

1. Open your **user** configuration `vnotex.json`.
2. Under `core.shortcuts` (application actions) or `editor.core.shortcuts` (editing actions), set the value to the key sequence you want, using the same `Modifier+Key` and comma-chord notation.
3. Restart VNote for the change to take effect.

Because shortcuts are just configuration, you can also carry your bindings between machines by syncing your user configuration — see [Settings](settings.md) and [Make VNote portable](settings.md#make-vnote-portable).

## Shortcuts and Vi mode

When [Vi mode](../editing/vi-mode.md) is enabled, Vi keys handle text editing **inside** a note (motions, operators, insert/normal/visual modes), while VNote's application shortcuts continue to handle app-level actions — switching notes, toggling docks, opening United Entry, applying snippets, and so on. The two layers coexist: Vi for editing text, VNote shortcuts for driving the application.

## Tips

- Learn the `Ctrl+G` prefix first — it unlocks snippets and United Entry, two of the biggest time-savers.
- Navigation mode (`Ctrl+G, W`) is the fastest way to reach a widget you rarely click.
- `Ctrl+G, A` jumps straight to the Notebooks dock without entering navigation mode.
- Reference shortcuts from [tasks](../productivity/tasks.md) with `${config:main.core.shortcuts.<Action>}` if you script around them.
- If a shortcut seems inactive, check the relevant shortcut table for conflicts, the Ctrl+Alt policy, and whether you restarted VNote after editing the file. Global hotkeys also require successful operating-system registration.

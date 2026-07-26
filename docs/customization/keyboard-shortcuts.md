# Keyboard Shortcuts

VNote is built to be driven from the keyboard. Almost every action has a shortcut, many actions use **chord shortcuts** (press one combination, then another), and the whole scheme is configurable. Combine this with [Vi mode](../editing/vi-mode.md) and you can work almost entirely without the mouse.

## Chord shortcuts

Some VNote shortcuts are chords, written as two parts separated by a comma. For example:

- `Ctrl+G, S` — open the [snippet](../editing/snippets.md) panel: press `Ctrl+G`, release, then press `S`.
- `Ctrl+G, I` — apply a snippet at the cursor.
- `Ctrl+G, G` — activate [United Entry](../search/united-entry.md).

The `Ctrl+G` prefix leads to a family of "go / global" actions; type the prefix and VNote shows you the follow-up keys.

## Where shortcuts are defined

Shortcuts live in the main configuration file `vnotex.json`, in two tables: application-level actions under `core.shortcuts`, and editor/editing actions (Save, bold, headings, Find, apply snippet, and so on) under `editor.shortcuts`. Each action maps to a key sequence, for example:

```json
"core": {
    "shortcuts": {
        "UnitedEntry": "Ctrl+G, G",
        "FullScreen": "F11"
    }
},
"editor": {
    "shortcuts": {
        "ApplySnippet": "Ctrl+G, I"
    }
}
```

To see the authoritative list of every action and its default binding, inspect the `core.shortcuts` and `editor.shortcuts` sections of your `vnotex.json` (the defaults are filled in by VNote). See [Settings](settings.md) for where these folders are and how the default/user layers work.

## Customizing a shortcut

1. Open your **user** configuration `vnotex.json`.
2. Under `core.shortcuts` (application actions) or `editor.shortcuts` (editing actions), set the value to the key sequence you want, using the same `Modifier+Key` and comma-chord notation.
3. Restart VNote for the change to take effect.

Because shortcuts are just configuration, you can also carry your bindings between machines by syncing your user configuration — see [Settings](settings.md) and [Make VNote portable](settings.md#make-vnote-portable).

## Shortcuts and Vi mode

When [Vi mode](../editing/vi-mode.md) is enabled, Vi keys handle text editing **inside** a note (motions, operators, insert/normal/visual modes), while VNote's application shortcuts continue to handle app-level actions — switching notes, toggling docks, opening United Entry, applying snippets, and so on. The two layers coexist: Vi for editing text, VNote shortcuts for driving the application.

## Tips

- Learn the `Ctrl+G` prefix first — it unlocks snippets and United Entry, two of the biggest time-savers.
- Reference shortcuts from [tasks](../productivity/tasks.md) with `${config:main.core.shortcuts.<Action>}` if you script around them.
- If a shortcut seems inactive, check for a conflict in `core.shortcuts` and confirm you restarted VNote after editing the file.

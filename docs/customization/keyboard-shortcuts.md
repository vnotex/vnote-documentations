# Keyboard Shortcuts

VNote is built to be driven from the keyboard. Almost every action has a shortcut, many actions use **chord shortcuts** (press one combination, then another), and the whole scheme is configurable. Combine this with [Vi mode](../editing/vi-mode.md) and you can work almost entirely without the mouse.

## Chord shortcuts

Some VNote shortcuts are chords, written as two parts separated by a comma. For example:

- `Ctrl+G, I` — open the [snippet](../editing/snippets.md) panel: press `Ctrl+G`, release, then press `I`.
- `Ctrl+G, G` — activate [United Entry](../search/united-entry.md).

The `Ctrl+G` prefix leads to a family of "go / global" actions; type the prefix and VNote shows you the follow-up keys.

## Where shortcuts are defined

Shortcuts live in the main configuration file `vnotex.json`, under `core.shortcuts`. Each action maps to a key sequence, for example:

```json
"core": {
    "shortcuts": {
        "UnitedEntry": "Ctrl+G, G",
        "FullScreen": "..."
    }
}
```

To see the authoritative, up-to-date list of every action and its default binding, open the `vnotex.json` in the **default** configuration folder — it is the complete reference and is annotated. See [Settings](settings.md) for where these folders are and how the default/user layers work.

## Customizing a shortcut

1. Open your **user** configuration `vnotex.json` (copy the key from the default configuration if it isn't there yet).
2. Change the value under `core.shortcuts` to the key sequence you want, using the same `Modifier+Key` and comma-chord notation.
3. Restart VNote for the change to take effect.

Because shortcuts are just configuration, you can also carry your bindings between machines by syncing your user configuration — see [Settings](settings.md) and [Make VNote portable](settings.md#make-vnote-portable).

## Shortcuts and Vi mode

When [Vi mode](../editing/vi-mode.md) is enabled, Vi keys handle text editing **inside** a note (motions, operators, insert/normal/visual modes), while VNote's application shortcuts continue to handle app-level actions — switching notes, toggling docks, opening United Entry, applying snippets, and so on. The two layers coexist: Vi for editing text, VNote shortcuts for driving the application.

## Tips

- Learn the `Ctrl+G` prefix first — it unlocks snippets and United Entry, two of the biggest time-savers.
- Reference shortcuts from [tasks](../productivity/tasks.md) with `${config:main.core.shortcuts.<Action>}` if you script around them.
- If a shortcut seems inactive, check for a conflict in `core.shortcuts` and confirm you restarted VNote after editing the file.

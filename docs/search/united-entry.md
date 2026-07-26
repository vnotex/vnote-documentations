# United Entry

**United Entry** is VNote's command-driven quick search. Instead of opening a panel and setting options, you activate a single box, type a short **entry command** followed by your **search criteria**, and jump straight to a folder, note, or file — all from the keyboard.

## Activation

By default, press `Ctrl+G, G` to activate United Entry. You can change this by editing `"UnitedEntry": "Ctrl+G, G"` in the configuration file (see [Settings](../customization/settings.md)) to whatever shortcut you prefer.

Once open, typing an entry command filters the box to that command's mode. Adding a **space** after the command triggers a second, detailed help display for that command.

## Entry commands

United Entry provides the following entry commands. Combine an entry command with a keyword to run the query.

| Command | Description                                             |
| ------- | ------------------------------------------------------ |
| `a`     | Search files by content in all notebooks               |
| `c`     | Search files by tag in the current notebook            |
| `d`     | Search files by content in the current notebook        |
| `e`     | Search folders/files by name in the current notebook   |
| `f`     | Search files by content in the current folder          |
| `find`  | Search files in a notebook                              |
| `g`     | Search files by content in buffers                      |
| `help`  | Help for United Entry                                   |
| `q`     | Search folders/files by name in all notebooks          |
| `r`     | Search folders/files by name in the current folder     |
| `t`     | Search files by name in buffers                         |
| `v`     | Search files by tag in the current folder              |
| `w`     | Search notebooks by name in all notebooks              |
| `z`     | Search files by tag in all notebooks                   |

## Examples

- `q 02` — find all folders/files containing `02` across all notebooks.
- `t task` — find the file containing `task` among the currently open buffers.
- `a interface` — search all notebooks for notes whose content contains `interface`.
- `z java` — find notes tagged `java` across all notebooks.

## Locating a result

!!! warning "This behaves differently per operating system"

    **macOS** — after results appear, press `Tab` to move the cursor into the results list below, then press `Enter` to open the target.

    **Windows** — after searching, the first result is selected by default, so you can press `Enter` to open it immediately, or move the selection first and then open.

## United Entry vs. the search panel

United Entry is fastest when you know what you want and want to jump. When you need browsable results and refinement options (regex, case, whole word), use the [Search Panel](search-panel.md) instead — both use the same underlying search.

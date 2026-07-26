# Vi Mode

VNote grew out of a Vim-inspired workflow, and it offers a built-in **Vi mode** for modal, keyboard-driven editing. If you think in terms of motions and operators, Vi mode lets you edit notes without leaving the home row.

## Enabling Vi mode

Turn Vi mode on in [Settings](../customization/settings.md). Once enabled, the editor starts in **normal mode**, and the usual modal editing applies across your notes.

## The modes

Vi mode brings the familiar states of a modal editor:

- **Normal** — keys are commands. Move and manipulate text without inserting it.
- **Insert** — type text as usual. Enter with `i`, `a`, `o`, and friends; leave with `Esc`.
- **Visual** — select text by motion, then act on the selection.
- **Command-line** — `:` commands for line-oriented actions.

## What's supported

Vi mode implements the motions and operators you reach for most:

- **Motions** — `h j k l`, `w b e`, `0 ^ $`, `gg G`, paragraph and search motions, and counts like `3w`.
- **Operators** — `d` (delete), `c` (change), `y` (yank), combined with motions and text objects (`diw`, `ci"`, `dd`, `yy`).
- **Editing** — `x`, `r`, `p`/`P`, `u` (undo) and redo, `.` to repeat.
- **Search** — `/` and `?` to search, `n`/`N` to repeat.
- **Registers and marks** for yanking and jumping.

It aims to cover everyday editing rather than every corner of Vim; deeply specialized plugins and Ex features are outside its scope.

## Vi mode and VNote shortcuts

Vi mode governs text editing inside a note. VNote's application-level actions — switching notes, opening panels, [United Entry](../search/united-entry.md), [snippets](snippets.md) — still use their own [keyboard shortcuts](../customization/keyboard-shortcuts.md), many of which are themselves chord-based (for example `Ctrl+G, I`). The two work together: Vi for editing, VNote shortcuts for navigating the app.

## If you don't use Vi

Vi mode is entirely optional and off unless you enable it. With it disabled, the editor behaves like a conventional text editor. Either way, see [Keyboard Shortcuts](../customization/keyboard-shortcuts.md) to customize how you drive VNote.

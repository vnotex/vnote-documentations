# Quick Note

**Quick Note** is for the thought you want to write down *now*, without deciding where it belongs. One shortcut creates a note in a predefined place, with a predefined name, and opens it ready to type in.

## Creating a quick note

Press `Ctrl+Alt+Q`, use **New → Quick Note** in the toolbar, or double-click the empty area of the tab bar. VNote creates the note from the current **scheme** and opens it immediately.

A scheme is what makes this instant: it answers "which folder?", "what name?" and "which template?" up front, so no dialog gets in your way.

## Quick note schemes

Schemes are configured under **Settings → Quick Access → Quick Note**. If you have not defined one yet, triggering Quick Note takes you straight to that settings page.

- **Scheme** — the list of schemes, with **New** and **Delete** buttons. Each scheme is an independent set of the fields below.
- **Folder** — where the note is created. Leave it **empty** to use the folder currently explored in the notebook explorer, which follows you around as you work. [Snippet](../editing/snippets.md) variables are supported, so `journal/%yyyy%/%MM%` files each note under the current year and month, creating the folders as needed. See [date and time placeholders](../editing/snippets.md#date-and-time-placeholders).
- **Note name** — the file name of the new note. It also accepts snippet variables, which is how the default name produces a distinct file every time.
- **Template** — the [template](../editing/templates.md) the note starts from. Leave it unset for an empty note.

## Ideas

- **Journal**: folder `journal/%yyyy%/%MM%` with a date-based note name and a journal template — one keystroke opens today's entry.
- **Inbox**: an empty folder field and a plain name, so notes land wherever you are currently working and get filed later.
- **Meeting notes**: a fixed folder plus a template that scaffolds attendees, agenda and actions.

Quick notes are ordinary notes: you can rename, move, tag and export them like anything else. See [Notebooks, Folders & Notes](../managing-notes/notebooks-folders-notes.md).

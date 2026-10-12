# Quick Note

**Quick Note** is for the thought you want to write down *now*, without deciding where it belongs. Choose a predefined scheme to create a note with a preset location, name, and template, ready to type in.

## Creating a quick note

Press the global `Ctrl+Alt+Q` shortcut, use **Quick Note** in the system-tray menu, choose **New → Quick Note** in the toolbar, or double-click the empty area of the tab bar. Select a **scheme** in the picker; VNote then creates and opens the note.

The global shortcut works even when the main window is hidden or minimized, provided VNote is running and the operating system registered the hotkey successfully. It uses `core.shortcuts.NewQuickNote`; conflicts with other applications or the [Ctrl+Alt shortcut policy](../customization/settings.md#general-settings) can prevent it from working. The tray and toolbar provide alternative entry points.

## Quick note schemes

Schemes are configured under **Settings → Quick Access → Quick Note**. If no scheme exists, VNote asks you to set one up first. Newly created schemes default to `my_notebook` under your Documents folder, like the first-run notebook; existing scheme folders are not changed.

- **Scheme** — the list of schemes, with **New** and **Delete** buttons. Each scheme is an independent set of the fields below.
- **Folder** — where the note is created. An absolute path may point to another open notebook or to an external folder; external notes open at their actual filesystem path. Leave it **empty** to use the folder currently explored in the notebook explorer, which follows you around as you work. [Snippet](../editing/snippets.md) variables are supported, so `journal/%yyyy%/%MM%` files each note under the current year and month, creating the folders as needed. See [date and time placeholders](../editing/snippets.md#date-and-time-placeholders).
- **Note name** — the file name of the new note. It also accepts snippet variables, which is how the default name produces a distinct file every time.
- **Template** — the [template](../editing/templates.md) the note starts from. Leave it unset for an empty note.
- **Open in detached window** — a per-scheme option, off by default. When enabled, notes open in their own window from any Quick Note entry point, including the tray and global shortcut.

## Ideas

- **Journal**: folder `journal/%yyyy%/%MM%` with a date-based note name and a journal template — choose the scheme to create today's entry.
- **Inbox**: an empty folder field and a plain name, so notes land wherever you are currently working and get filed later.
- **Meeting notes**: a fixed folder plus a template that scaffolds attendees, agenda and actions.

Quick notes created inside notebooks can be managed like other notes there. Notes created in external folders do not gain notebook-only features such as tags. See [Notebooks, Folders & Notes](../managing-notes/notebooks-folders-notes.md).

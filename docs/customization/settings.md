# Settings

Most of VNote's behavior can be adjusted, either through the **Settings** tab or by editing configuration files directly. This page explains how VNote's configuration is layered, where the files live, and how to make VNote portable.

## The Settings tab

Open **Settings** from the toolbar or menu and it opens as a tab in the main window, where you can change common options — appearance and [theme](themes-and-styles.md), editor behavior, [Vi mode](../editing/vi-mode.md), read/render options, [image host](../editing/images-and-image-host.md), and more. For anything not exposed there, you can edit the configuration files described below.

![The Settings tab](../assets/screenshots/settings.webp){ .screenshot loading=lazy }

## Layers of configuration

VNote's configuration is layered, applied in order:

- **Default configuration** — the application's built-in defaults. These live inside the program itself; there is no annotated file on disk to copy from. To customize a value, set it in your *user configuration* file, where it overrides the default.
- **User configuration** — your overrides in the main `vnotex.json` file, in the user configuration folder. Anything here takes precedence over the defaults.
- **Session configuration** — session state such as the notebook list and the main window's geometry. This is the `session.json` file. VNote writes it continuously while running and flushes it on close, so close VNote before editing it by hand.

## What's in the configuration folder

The configuration folder contains several folders and the main file:

```
.
├── dicts               (dictionaries for spellcheck)
├── syntax-highlighting (Kate syntax-highlighting files for the text editor)
├── tasks               (task definitions; see Tasks)
├── themes              (VNote themes)
├── web                 (resources used by read mode)
└── vnotex.json         (main configuration file)
```

To customize the fields in `vnotex.json`, add or edit the keys you need — VNote merges your file over its built-in defaults. Related per-feature folders you will see referenced elsewhere include `tasks` (see [Tasks](../productivity/tasks.md)) and `templates` (see [Templates](../editing/templates.md)).

## Make VNote portable

You can bundle the configuration next to the executable so the whole setup travels together — for example on a USB drive:

1. Close VNote first.
2. Create a folder named `config` next to the executable (such as `vnote.exe`).
3. Inside it, VNote uses two subfolders: `app` (application settings, including `vnotex.json`) and `local` (session and cache, including `session.json`). VNote creates them on first run.

When a `config` folder exists next to the executable at startup, VNote reads and writes configuration there instead of the system-wide location.

## Related customization

- [Themes & Styles](themes-and-styles.md) — change the look of the interface, editor, and read mode.
- [Keyboard Shortcuts](keyboard-shortcuts.md) — remap actions, including [United Entry](../search/united-entry.md).
- If VNote crashes after a version update, deleting `vnotex.json` from the user configuration folder is a common fix — see the [FAQ](../help/faq.md).

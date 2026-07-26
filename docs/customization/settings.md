# Settings

Most of VNote's behavior can be adjusted, either through the **Settings** dialog or by editing configuration files directly. This page explains how VNote's configuration is layered, where the files live, and how to make VNote portable.

## The Settings dialog

Open **Settings** from the toolbar or menu to change common options — appearance and [theme](themes-and-styles.md), editor behavior, [Vi mode](../editing/vi-mode.md), read/render options, [image host](../editing/images-and-image-host.md), and more. For anything not exposed in the dialog, you can edit the configuration files described below.

## Layers of configuration

VNote has three layers of configuration, applied in order:

- **Default configuration** — the application's built-in defaults. **Do not edit these files**; they are overwritten on every version update. To customize a value, copy the relevant file into the *user configuration* folder and change it there.
- **User configuration** — your overrides. Anything here takes precedence over the defaults.
- **Session configuration** — session state such as the notebook list and the main window's geometry. This is the `session.json` file in the user configuration folder. VNote **writes this file on close**, so close VNote before editing it by hand.

## What's in the configuration folder

The configuration folder contains several folders and a main file:

```
.
├── dicts               (dictionaries for spellcheck)
├── docs                (docs VNote uses for in-app help)
├── syntax-highlighting (Kate syntax-highlighting files for the text editor)
├── themes              (VNote themes)
├── web                 (resources used by read mode)
└── vnotex.json         (main configuration file)
```

For the `vnotex.json` fields, refer to the copy in the **default** configuration folder — it contains comments explaining each field. Related per-feature folders you will see referenced elsewhere include `tasks` (see [Tasks](../productivity/tasks.md)) and `templates` (see [Templates](../editing/templates.md)).

## Make VNote portable

You can bundle the configuration next to the executable so the whole setup travels together — for example on a USB drive:

1. Close VNote first.
2. Copy the **default** configuration folder `VNote` next to the executable (such as `vnote.exe`) and rename it to `vnotex_files`.
3. Copy the **user** configuration folder `VNote` next to the executable and rename it to `user_files`.

VNote will then read and write configuration from these local folders instead of the system-wide location.

## Related customization

- [Themes & Styles](themes-and-styles.md) — change the look of the interface, editor, and read mode.
- [Keyboard Shortcuts](keyboard-shortcuts.md) — remap actions, including [United Entry](../search/united-entry.md).
- If VNote crashes after a version update, deleting `vnotex.json` from the user configuration folder is a common fix — see the [FAQ](../help/faq.md).

# Command Line

VNote can be launched from a terminal, a script, or your desktop's "Open with" menu. Passing file paths opens them directly, and a few options change how VNote starts up.

```bash
vnote [options] [paths...]
```

## Opening files

Any positional argument is treated as a file or folder to open. Paths may be relative or absolute, and the files do not have to belong to a notebook — VNote opens them as standalone buffers.

If VNote is already running, a second invocation does not start a new process: the paths are forwarded to the running instance, which opens them and raises its window.

## Options

| Option | What it does |
|--------|--------------|
| `-h`, `--help` | Print the option list and exit. |
| `-v`, `--version` | Print the version and exit. |
| `--verbose` | Print more logs. |
| `--log-stderr` | Log to stderr instead of only to the log file. |
| `--quiet` | Suppress non-critical console logs. |
| `--watch-themes` | Watch the theme folder for changes and reload themes as you edit them. Useful when authoring a [theme](../customization/themes-and-styles.md). |
| `--detached-view` | Open the given files in a detached view split. |

## Detached view

With `--detached-view`, the files are opened in a separate top-level window instead of a tab in the main window, and the main window is not raised. This makes VNote a convenient viewer for a file you want side by side with another application:

```bash
vnote --detached-view notes/todo.md
```

Detached windows are described in [Editor Basics](../editing/editor-basics.md#detached-windows), where you can also detach a tab that is already open.

!!! note "Rarely needed"
    VNote also accepts a few QtWebEngine flags — `--remote-debugging-port <port_number>`, `--no-sandbox` and `--disable-gpu`. They are not listed in `--help` and exist for debugging and for working around graphics-driver problems.

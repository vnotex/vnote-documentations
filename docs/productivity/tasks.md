# Tasks

VNote includes a simple **task** system, modeled on [VSCode Tasks](https://code.visualstudio.com/docs/editor/tasks), that lets you run third-party programs and scripts from within VNote. Use it to compile the current note, run a local server, open a file in another editor, drive git, or anything else you can script.

## How tasks are loaded

VNote loads tasks from three locations, so tasks can be shipped with the app, shared across your setup, or scoped to one notebook:

- `default_config_folder/tasks` — built-in tasks
- `user_config_folder/tasks` — your personal tasks
- `notebook_config_folder/tasks` — tasks defined by a specific notebook

Each task is defined by a `*.json` entry file. See [Settings](../customization/settings.md) for where these folders are.

## A simple task

Click **Add Task** on the task menu to open the user tasks folder. Create a folder named `hello`, and inside it a file `hello.json`:

```json
{
    "command": "echo 'Hello Tasks'"
}
```

Reload tasks from the menu and a `hello` task appears. Click it to run.

### Customize the menu item

```json
{
    "label": "Hello",
    "icon": "tasks-solid.svg",
    "shortcut": "Alt+H, T",
    "command": "echo",
    "args": ["Hello tasks!"]
}
```

Save the icon file (`tasks-solid.svg`) next to the JSON entry file.

### Sub-tasks

Tasks can nest to any depth; sub-tasks inherit most properties from their parent.

```json
{
    "label": "Hello Tasks",
    "icon": "tasks-solid.svg",
    "command": "echo",
    "args": ["Hello tasks!"],
    "tasks": [
        { "label": "Hello Cat", "icon": "cat-solid.svg", "args": ["Hello cat!"] },
        { "label": "Hello Dove", "icon": "dove-solid.svg", "args": ["Hello dove!"] }
    ]
}
```

### Command types

The `type` property controls how a command runs:

- `shell` (default) — run the command through a shell.
- `process` — run the command as a standalone program.

```json
{
    "type": "process",
    "label": "Open File with",
    "args": ["${buffer}"],
    "tasks": [
        { "label": "VS Code", "icon": "vscode.svg", "command": "C:\\...\\Code.exe" }
    ]
}
```

VNote does not provide a terminal, so to run something in a terminal use `start` (Windows), `gnome-terminal`, `konsole`, and the like.

### Localization and platform-specific options

Provide a locale-string object to localize a field, and use `windows`/`linux`/`osx` keys for per-platform options.

```json
{
    "label": { "en_US": "Hello", "zh_CN": "你好" },
    "windows": { "command": "C:\\...\\typora.exe" },
    "linux": { "command": "/usr/bin/typora" }
}
```

## Task options

A task supports many options (`[m]` marks mandatory, `[l]` marks localizable):

- `version` — the version of the task file
- `label[l]` — the task name
- `type` — `shell` (default) or `process`
- `command[l]` — the command to execute
- `args[l]` — arguments passed to the command
- `options`
    - `cwd` — working directory (falls back to notebook root, then buffer folder, then task file folder)
    - `env` — environment variables
    - `shell` — `executable` and `args` for `shell` tasks (`Powershell.exe` on Windows, `/bin/bash` on Linux/macOS by default)
- `tasks` — sub-tasks
- `inputs` — input variables
    - `id[m]`, `type` (`promptString`/`pickString`), `description[l]`, `default[l]`, `password`, `options[l]`
- `windows` / `linux` / `osx` — per-platform options

## Variables

Tasks can use VNote variables as `${variableName}` in `command`, `args`, `options.cwd`, and `options.env`.

**Notebook:** `notebookFolder`, `notebookFolderName`, `notebookName`, `notebookDescription`.

**Buffer:** `buffer`, `bufferNotebookFolder`, `bufferRelativePath`, `bufferName`, `bufferBaseName`, `bufferDir`, `bufferExt`, `selectedText`.

**Task/paths:** `cwd`, `taskFile`, `taskDir`, `exeFile`, `pathSeparator`, `notebookTaskFolder`, `taskFolder`, `themeFolder`.

**Special:**

- `${magic:snippet_name}` — call a VNote [snippet](../editing/snippets.md).
- `${env:env_name}` — read an environment variable.
- `${config:[main|session].json_path}` — read a VNote configuration value, e.g. `${config:main.core.shortcuts.FullScreen}`.
- `${shell:command}` — substitute the output of a shell command.

### Input variables

Prompt the user with `${input:input_id}`:

```json
{
    "command": "echo",
    "args": ["${input:what}"],
    "inputs": [
        { "id": "what", "type": "promptString", "description": "Type something." }
    ]
}
```

`pickString` prompts a selection instead of free text.

### Shell variables

Run a shell command and use its output with `${shell:command}`:

- `${shell:git rev-parse --abbrev-ref HEAD}` → `master`
- `${shell:whoami}` → your user name

## Examples

Compile and run the current file (Windows):

```json
{
    "command": "g++ \"${buffer}\" -o \"${bufferBaseName}\"; if ($?) { start cmd \"/c `\"${bufferBaseName}`\" & pause\" }"
}
```

Serve the current folder over HTTP:

```json
{
    "command": "start cmd.exe \"/c python -m http.server\" ; start http://localhost:8000"
}
```

There is also a built-in `Git` task in the default configuration task folder you can use as a reference.

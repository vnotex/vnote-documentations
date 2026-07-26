# 任务

VNote 内置了一套简单的**任务**系统，其设计参照 [VSCode Tasks](https://code.visualstudio.com/docs/editor/tasks)，让你能在 VNote 内运行第三方程序和脚本。用它来编译当前笔记、运行本地服务器、用其他编辑器打开文件、驱动 git，或任何你能编写脚本完成的事。

## 任务如何加载

VNote 从三个位置加载任务，因此任务既可以随应用分发，也可以在你的整个环境中共享，或限定于某个笔记本：

- `default_config_folder/tasks`——内置任务
- `user_config_folder/tasks`——你的个人任务
- `notebook_config_folder/tasks`——某个特定笔记本定义的任务

每个任务由一个 `*.json` 入口文件定义。这些文件夹的位置参见[设置](../customization/settings.md)。

## 一个简单的任务

在任务菜单中点击**添加任务**以打开用户任务文件夹。创建一个名为 `hello` 的文件夹，并在其中创建文件 `hello.json`：

```json
{
    "command": "echo 'Hello Tasks'"
}
```

从菜单重新加载任务，一个 `hello` 任务便会出现。点击它即可运行。

### 自定义菜单项

```json
{
    "label": "Hello",
    "icon": "tasks-solid.svg",
    "shortcut": "Alt+H, T",
    "command": "echo",
    "args": ["Hello tasks!"]
}
```

把图标文件（`tasks-solid.svg`）与 JSON 入口文件放在一起。

### 子任务

任务可以任意层级嵌套；子任务会从父任务继承大部分属性。

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

### 命令类型

`type` 属性控制命令如何运行：

- `shell`（默认）——通过 shell 运行命令。
- `process`——将命令作为独立程序运行。

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

VNote 不提供终端，因此若要在终端中运行程序，请使用 `start`（Windows）、`gnome-terminal`、`konsole` 之类。

### 本地化与平台专属选项

提供一个 locale-string 对象来本地化某个字段，并用 `windows`/`linux`/`osx` 键设置各平台的选项。

```json
{
    "label": { "en_US": "Hello", "zh_CN": "你好" },
    "windows": { "command": "C:\\...\\typora.exe" },
    "linux": { "command": "/usr/bin/typora" }
}
```

## 任务选项

任务支持许多选项（`[m]` 表示必填，`[l]` 表示可本地化）：

- `version`——任务文件的版本
- `label[l]`——任务名称
- `type`——`shell`（默认）或 `process`
- `command[l]`——要执行的命令
- `args[l]`——传给命令的参数
- `options`
    - `cwd`——工作目录（依次回退到笔记本根目录、缓冲区文件夹、任务文件所在文件夹）
    - `env`——环境变量
    - `shell`——`shell` 类型任务的 `executable` 和 `args`（Windows 默认 `Powershell.exe`，Linux/macOS 默认 `/bin/bash`）
- `tasks`——子任务
- `inputs`——输入变量
    - `id[m]`、`type`（`promptString`/`pickString`）、`description[l]`、`default[l]`、`password`、`options[l]`
- `windows` / `linux` / `osx`——各平台选项

## 变量

任务可在 `command`、`args`、`options.cwd` 和 `options.env` 中以 `${variableName}` 使用 VNote 变量。

**笔记本：**`notebookFolder`、`notebookFolderName`、`notebookName`、`notebookDescription`。

**缓冲区：**`buffer`、`bufferNotebookFolder`、`bufferRelativePath`、`bufferName`、`bufferBaseName`、`bufferDir`、`bufferExt`、`selectedText`。

**任务/路径：**`cwd`、`taskFile`、`taskDir`、`exeFile`、`pathSeparator`、`notebookTaskFolder`、`userTaskFolder`、`appTaskFolder`、`userThemeFolder`、`appThemeFolder`、`userDocsFolder`、`appDocsFolder`。

**特殊：**

- `${magic:snippet_name}`——调用 VNote [代码片段](../editing/snippets.md)。
- `${env:env_name}`——读取环境变量。
- `${config:[main|session].json_path}`——读取 VNote 配置值，例如 `${config:main.core.shortcuts.FullScreen}`。

### 输入变量

用 `${input:input_id}` 提示用户输入：

```json
{
    "command": "echo",
    "args": ["${input:what}"],
    "inputs": [
        { "id": "what", "type": "promptString", "description": "输入一些内容。" }
    ]
}
```

`pickString` 会提示从选项中选择，而非自由输入。

### Shell 变量

运行一条 shell 命令并用 `${shell:command}` 使用其输出：

- `${shell:git rev-parse --abbrev-ref HEAD}` → `master`
- `${shell:whoami}` → 你的用户名

## 示例

编译并运行当前文件（Windows）：

```json
{
    "command": "g++ \"${buffer}\" -o \"${bufferBaseName}\"; if ($?) { start cmd \"/c `\"${bufferBaseName}`\" & pause\" }"
}
```

在 HTTP 上提供当前文件夹：

```json
{
    "command": "start cmd.exe \"/c python -m http.server\" ; start http://localhost:8000"
}
```

默认配置的任务文件夹中还有一个内置的 `Git` 任务，可作为参考。

# 统一入口

**统一入口**是 VNote 命令驱动的快捷搜索。你无需打开面板再设置选项，而是激活单个输入框，输入一条简短的**入口命令**加上**搜索条件**，即可直接跳转到某个文件夹、笔记或文件——全程用键盘完成。

## 激活方式

默认按 `Ctrl+G, G` 激活统一入口。你可以在配置文件中修改 `"UnitedEntry": "Ctrl+G, G"`（参见[设置](../customization/settings.md)），换成你习惯的快捷键。

打开后，输入某个入口命令会把输入框筛选到该命令的模式。在命令后加一个**空格**会触发第二段、更详细的帮助显示。

## 入口命令

统一入口内置了四条命令，另外还提供了几个用于常见搜索的短别名。将命令与关键词组合即可执行查询。

内置命令：

| 命令      | 描述                     |
| --------- | ------------------------ |
| `find`    | 在笔记本中搜索文件       |
| `help`    | 统一入口的帮助信息       |
| `history` | 最近打开的文件           |
| `windows` | 跨工作区打开的窗口       |

默认别名（常见 `find` 查询的快捷方式）：

| 别名 | 描述                             | 展开为                                  |
| ---- | -------------------------------- | --------------------------------------- |
| `n`  | 在当前笔记本中按名称搜索文件     | `find --scope notebook --object name`   |
| `g`  | 在当前笔记本中按内容搜索文件     | `find --scope notebook --object content`|
| `b`  | 在打开的缓冲区中按内容搜索文件   | `find --scope buffer --object content`  |
| `f`  | 在当前文件夹中按名称搜索文件     | `find --scope folder --object name`     |

你也可以直接调用 `find` 并使用选项进行完全控制：

- `-s, --scope`——`buffer`、`folder`、`notebook` 或 `all_notebook`。
- `-b, --object`——`name`、`content`、`tag` 或 `path`。
- `-p, --pattern`——用于限定搜索范围的通配符文件模式。
- `-c, --case-sensitive`——精确区分大小写。
- `-r, --regular-expression`——把关键词视为正则表达式。

## 添加你自己的别名

四个默认别名只覆盖了 `find` 能做的一小部分。你可以在配置文件的 `core.unitedEntry.alias` 之下定义自己的单字母（或短）别名（参见[设置](../customization/settings.md)）。每个别名是一个对象，包含 `name`（你要输入的内容）、`description`（显示在帮助列表中）和 `value`（它展开成的 `find` 命令）：

```json
"core": {
    "unitedEntry": {
        "alias": [
            {
                "name": "q",
                "description": "Search for files by name in all notebooks",
                "value": "find --scope all_notebook --object name"
            },
            {
                "name": "a",
                "description": "Search for files by content in all notebooks",
                "value": "find --scope all_notebook --object content"
            },
            {
                "name": "z",
                "description": "Search for files by tag in all notebooks",
                "value": "find --scope all_notebook --object tag"
            },
            {
                "name": "e",
                "description": "Search for files by name in current notebook",
                "value": "find --scope notebook --object name"
            },
            {
                "name": "c",
                "description": "Search for files by tag in current notebook",
                "value": "find --scope notebook --object tag"
            },
            {
                "name": "t",
                "description": "Search for files by name in open buffers",
                "value": "find --scope buffer --object name"
            }
        ]
    }
}
```

把任意 `--scope` 与任意 `--object`（`name`、`content`、`tag`、`path`）自由组合，即可搭建你最常用的快捷方式。新别名需重启 VNote 后生效。

!!! note "从旧版 VNote 迁移别名"
    旧版 VNote 使用顶层的 `united_entry.alias` 键，以及 `--target file|folder|notebook` 选项。在当前版本中，别名位于 `core.unitedEntry.alias` 之下，且 `find` 不再接受 `--target`——改用 `--scope` 和 `--object`。

## 查询示例

- `n 02`——在当前笔记本中查找名称包含 `02` 的文件。
- `g interface`——在当前笔记本中搜索内容包含 `interface` 的笔记。
- `b task`——在当前打开的缓冲区中查找 `task`。
- `find -b tag -s all_notebook java`——在所有笔记本中查找带 `java` 标签的笔记。

## 定位结果

!!! warning "不同操作系统的行为有所不同"

    **macOS**——出现结果后，按 `Tab` 将光标移入下方的结果列表，再按 `Enter` 打开目标。

    **Windows**——搜索完成后默认选中第一个结果，因此你可以直接按 `Enter` 立即打开，也可以先移动选择再打开。

## 统一入口与搜索面板

当你明确知道要找什么并想直接跳转时，统一入口最为快捷。当你需要可浏览的结果和优化选项（正则、大小写）时，请改用[搜索面板](search-panel.md)——两者使用相同的底层搜索。

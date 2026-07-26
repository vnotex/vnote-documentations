# 键盘快捷键

VNote 生来就是为键盘操作而设计的。几乎每个操作都有快捷键，许多操作使用**组合序列快捷键**（chord，先按一个组合，再按另一个），而且整套方案都可配置。将其与 [Vi 模式](../editing/vi-mode.md)结合，你几乎可以完全脱离鼠标工作。

## 组合序列快捷键

VNote 的部分快捷键是组合序列，写作以逗号分隔的两部分。例如：

- `Ctrl+G, S`——打开[代码片段](../editing/snippets.md)面板：按 `Ctrl+G`，松开，再按 `S`。
- `Ctrl+G, I`——在光标处应用一个片段。
- `Ctrl+G, G`——激活[统一入口](../search/united-entry.md)。

`Ctrl+G` 前缀引出一系列「跳转 / 全局」操作；输入前缀后，VNote 会向你显示后续按键。

## 快捷键在哪里定义

快捷键位于主配置文件 `vnotex.json` 中，分为两张表：应用级操作在 `core.shortcuts` 之下，编辑器/编辑类操作（保存、加粗、标题、查找、应用片段等）在 `editor.shortcuts` 之下。每个操作映射到一个按键序列，例如：

```json
"core": {
    "shortcuts": {
        "UnitedEntry": "Ctrl+G, G",
        "FullScreen": "F11"
    }
},
"editor": {
    "shortcuts": {
        "ApplySnippet": "Ctrl+G, I"
    }
}
```

要查看每个操作及其默认绑定的权威列表，请查看你的 `vnotex.json` 中的 `core.shortcuts` 和 `editor.shortcuts` 段落（默认值由 VNote 填入）。这些文件夹的位置以及默认/用户层的工作方式参见[设置](settings.md)。

## 自定义快捷键

1. 打开你的**用户**配置 `vnotex.json`。
2. 在 `core.shortcuts`（应用操作）或 `editor.shortcuts`（编辑操作）下，把值改为你想要的按键序列，使用相同的 `Modifier+Key` 与逗号组合序列写法。
3. 重启 VNote 使更改生效。

由于快捷键只是配置，你也可以通过同步用户配置在机器之间携带你的绑定——参见[设置](settings.md)与[让 VNote 便携化](settings.md#make-vnote-portable)。

## 快捷键与 Vi 模式

启用 [Vi 模式](../editing/vi-mode.md)后，Vi 按键处理笔记**内部**的文本编辑（移动、操作符，插入/普通/可视模式），而 VNote 的应用快捷键继续处理应用级操作——切换笔记、切换停靠部件、打开统一入口、应用片段等等。两层共存：Vi 用于编辑文本，VNote 快捷键用于操控应用。

## 小贴士

- 先掌握 `Ctrl+G` 前缀——它解锁片段与统一入口这两项最省时的功能。
- 如果你围绕快捷键编写脚本，可在[任务](../productivity/tasks.md)中用 `${config:main.core.shortcuts.<Action>}` 引用它们。
- 如果某个快捷键似乎无效，检查 `core.shortcuts` 中是否存在冲突，并确认编辑文件后已重启 VNote。

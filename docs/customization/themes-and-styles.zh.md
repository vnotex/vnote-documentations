# 主题与样式

**主题**控制 VNote 的外观——界面、编辑器与阅读模式，以及代码块的语法高亮。VNote 自带若干主题，而且由于主题只是一个装着文件的文件夹，你可以复制一份并加以调整，把 VNote 变成你自己的样子。

## 主题

一个主题对应 `themes` 文件夹内的一个文件夹。在**设置**对话框中选择和管理主题。配置文件夹与主题文件夹的位置参见[设置](settings.md)。

![应用了 Pure 主题的主界面](../assets/screenshots/main-pure.webp){ .screenshot loading=lazy }

### 添加主题

最简单的起步方式是基于现有主题：

1. 复制一个你喜欢的主题的文件夹。
2. 把它粘贴到**用户配置**文件夹下的 `themes` 文件夹中。
3. 重命名该文件夹——这将成为主题的名称。

然后按喜好编辑其中的文件。

### 主题里有什么

主题的关键文件：

- `palette.json`——主题的调色板；定义在整个主题中复用的颜色。
- `interface.qss`——一份 [Qt 样式表](http://doc.qt.io/qt-5/stylesheet-reference.html)，为每个控件设置样式；它使用 `palette.json` 中的颜色。
- `text-editor.theme`——文本编辑器（以及 Markdown 编辑器）的主题。
- `web.css`——Markdown**阅读模式**的样式表。
- `highlight.css`——阅读模式代码块的语法高亮（VNote 在阅读模式下使用 [Prism](https://prismjs.com/)）。
- `icons/`——可选的自定义图标文件夹。

## 自定义字体

### 阅读模式

阅读模式字体在 `web.css` 中设置。正文文本使用 `body` 上的 `font-family` 和 `font-size`：

```css
body {
    font-family: -apple-system, "Noto Sans", "Segoe UI", sans-serif;
    font-size: 16px;
    line-height: 1.5;
}
```

代码字体在 `code` 和 `pre code` 上设置：

```css
code {
    font-family: Consolas, Monaco, Monospace, Courier;
}
```

带语法高亮的代码块在 `highlight.css` 中设置样式（`code[class*="language-"]` / `pre[class*="language-"]` 规则）。

### 文本与 Markdown 编辑器

编辑器字体在 `text-editor.theme` 中设置。在编辑器的 `Text` 样式下设置 `font-family` 和 `font-size`：

```json
{
    "editor-styles": {
        "Text": {
            "font-family": "Consolas, Monaco, Monospace, Courier New",
            "font-size": 12
        }
    }
}
```

Markdown 编辑器有一个对应的 `markdown-editor-styles` 块。

### 界面字体

要更改界面字体（菜单、树），用 Qt 样式表规则编辑 `interface.qss`。[Qt 文档](https://doc.qt.io/qt-5/stylesheet-examples.html)提供了许多示例。

```css
QWidget { font-size: 12pt; }

QTreeView, QListView { font-size: 12pt; }

vnotex--NotebookNodeExplorer QTreeView { font-size: 14pt; }
```

## 自定义图标

把图标文件放进主题的 `icons` 文件夹即可覆盖 VNote 的图标。图标文件名的完整列表参见 [VNote 源码中的 icons](https://github.com/vnotex/vnote/tree/master/src/data/core/icons)。

一个典型的主题目录：

```
.
├── cover.png          （可选）
├── highlight.css
├── icons
│   ├── ***.svg
│   └── ***.svg
├── interface.qss
├── palette.json
├── text-editor.theme
└── web.css
```

一些常被替换的图标：

- **笔记：**`folder_node.svg`（文件夹）、`file_node.svg`（笔记）。
- **顶部菜单栏：**`new_note.svg`、`quick_access_menu.svg`、`united_entry.svg`、`expand.svg`、`settings.svg`、`task_dock.svg`、`split_menu.svg`、`search.svg`、`menu.svg`。
- **左侧导航栏：**`navigation_dock.svg`、`history_dock.svg`、`tag_dock.svg`、`search_dock.svg`、`snippet_dock.svg`。

## 应用导出样式

由于阅读模式使用这些样式，它们也驱动[导出](../productivity/export.md)——你可以在导出对话框中为导出的输出选择不同的渲染样式。

# Markdown 语法

VNote 以 **Markdown** 为核心设计——这是一种轻量、易用的书写语法——其编辑器会在你输入时就地高亮这些语法，让笔记无需单独预览也保持易读。Markdown 并没有唯一的标准，很多编辑器都会添加自己的扩展；VNote 支持那些被广泛使用的基本语法，以及少量流行的扩展。本页是 VNote 所能识别语法的实用参考。编辑体验本身参见[编辑器基础](editor-basics.md)。

## 标题

```md
# This is an <h1> tag
## This is an <h2> tag
###### This is an <h6> tag
```

- `#` 之后需要至少一个空格。
- 一个标题应该占一整行。

标题会汇入可交互的[大纲](editor-basics.md)，因此用它们来组织长笔记的结构。

在编辑模式下，右键点击 ATX 标题（以 `#` 开头的行）可以使用**复制链接（Copy Link）**，它会复制笔记路径与该标题的锚点——与阅读模式使用的锚点一致——可直接粘贴到另一篇笔记中作为链接。

自动[源码标题编号](editor-basics.md#heading-numbering)仅适用于 ATX 标题。Setext 标题（文字下一行用 `===` 或 `---` 作下划线）不会被编辑器的源码编号功能编号。

## 强调

```md
*This text will be italic*
_This text will be italic_

**This text will be bold**
__This text will be bold__
```

- VNote 推荐使用 `*`。
- 如果渲染错误，请尝试在第一个 `*` 之前以及最后一个 `*` 之后添加一个空格。如果被标记的文本以全角符号开始或结尾，通常都需要前后添加一个空格。

## 列表

### 无序列表

```md
* Item 1  
只是一段在 Item 1 下面的文字。注意上面一行结尾有两个空格。
* Item 2
    * Item 2a
    * Item 2b
* Item 3

使用一个空行来结束一个列表。
```

### 有序列表

```md
1. Item 1
1. Item 2  
注意，列表前面的序号其实是无关紧要的，渲染时 Markdown 会自动修改该序号。
3. Item 3
    1. Item 3a
    2. Item 3b
4. Item 4
```

启用 **设置 → Markdown 编辑器 → 自动重新编号有序列表（Automatically renumber ordered lists）**（默认开启）后，编辑会保持源码中的列表编号连续，并保留各列表的起始数字；仅加载笔记不会重新编号。列表延续与缩进遵循列表结构，也支持 Vi 模式的另起一行操作。这与[标题编号](editor-basics.md)相互独立。

## 表格

```md
| col 1 | col 2 | col 3 |
| --- | --- | --- |
| cell1 | cell2 | cell3 |
| cell4 | cell5 | cell6 |
```

使用 Markdown 工具栏上的**插入表格（Insert Table）**，通过尺寸选择器指定行数与列数。表格可以紧接段落或列表项文字，无需空行。[交互式表格预览](editor-basics.md)的单元格支持行内图片和数学公式；**插入图片**会作用于选中的单元格，包括 Base64 图片或图床上传。单行 `$$…$$` 公式采用块级公式的排版样式，但在单元格、段落或列表中仍以内联方式放置。

## 图片和链接

```md
![Image Alt Text](/url/to/image.png "Optional Title")

![Image Alt Text](/url/to/image.png "Image specified with width and height" =800x600)

![Image Alt Text](/url/to/image.png =800x600)

![Image Alt Text](/url/to/image.png "Image specified with width" =800x)

![Image Alt Text](/url/to/image.png "Image specified with height" =x600)

[Link Text](/url/of/the/link)
```

- `=宽x高` 后缀用于设置渲染时的图片尺寸；省略其中一侧即可只设置一个维度。
- VNote 的 **Base64** 插入功能生成的参考式图片链接受支持；参见[图片存储方式](images-and-image-host.md)。
- 在 Markdown 编辑器中，用 `Ctrl+单击` 跳转链接；普通单击只移动光标。支持的本地文件可在可编辑的[链接预览](editor-basics.md#link-previews)中打开；右键菜单的**打开链接（Open Link）**则绕过预览，在应用内打开目标时始终使用新标签页，不受新标签页偏好影响。

你也可以直接粘贴图片，VNote 会把文件保存到笔记本中并替你写好链接。粘贴、本地存储与图床参见[图片与图床](images-and-image-host.md)。

```md
![替代文本](vx_assets/example.png)
```

链接和标记的显示由 Markdown 工具栏的**菜单（Menu）→ 标记隐藏（Markers Concealment）**预设控制，不再使用独立的长链接开关。**温和（Passive）**显示语法，同时缩短较长的链接、图片和引用网址；**适中（Moderate）**与**强烈（Aggressive）**还会隐藏支持的标记和链接语法。选择**无（None）**可显示全部源码。光标移入时的行为及编辑体验选择框参见[标记隐藏](editor-basics.md#markers-concealment)。

## 块引用

```md
As VNote suggests:

> VNote is the best Markdown note-taking application
> ever.  
>
> There are two spaces after `ever.` above to insert a
> new line.

It also suggests:

> VNote is good.  
Here is another sentence within the quote.
```

- `>` 标记后面需要至少一个空格。
- 多行连续的引用可以只在第一行添加标记。
- 在块引用中按 `Enter` 会自动延续引用，替你插入 `>` 标记；嵌套引用与惰性延续的引用同样适用。在空的引用行上按 `Enter` 即可退出引用。

## 代码块

用三个反引号（或波浪号）围栏代码，并写明语言以获得语法高亮：

````md
```python
def hello():
    print("Hello, VNote")
```
````

```md
~~~cpp
// This is another fenced code block.
~~~
```

- `lang` 可选；如果不指定，VNote 不会尝试高亮代码。支持的语言列表参见 [Prism](https://prismjs.com/#supported-languages)。
- 总是在一个代码块前面添加一个空行是一个不错的实践。

在**阅读模式**中，右键点击代码块，在**导出（Export）**下方选择**折叠（Collapse）**或**展开（Expand）**来控制显示。这与编辑模式中的源码折叠相互独立，不会改写代码。从网页导入代码时，[解析为 Markdown 并粘贴](editor-basics.md#rich-text-and-html-paste)会保留受支持的 HTML 代码块、缩进、语言提示和内嵌围栏。

## 行内代码

```md
Here is an `inline code`.
```

如果想输入一个 `` ` ``，需要使用两个 `` ` `` 来括住它（`` `` ` `` ``）。要输入两个 `` ` ``，则需要使用三个 `` ` ``。

## 删除线

```md
Here is a ~~text~~ with strikethrough.
```

## 任务列表

```md
* [x] this is a complete item.
* [ ] this is an incomplete item.
```

复选框是可交互的：在**阅读模式**下或编辑模式的原位预览中点击它，VNote 会切换其状态并改写对应的源码行，同时把笔记标记为已修改。只要编辑器的文档处于活动状态，这就是一次可撤销的编辑，按 `Ctrl+Z` 即可还原。只读笔记会拒绝切换并提示该笔记为只读。此功能无需配置——参见[编辑器基础](editor-basics.md)。

默认快捷键为 `Ctrl+8`（未完成任务列表项）和 `Ctrl+9`（已完成任务列表项）。从 4.13 起，这两个按键用于任务列表，不再用于无序/有序列表；参见[键盘快捷键](../customization/keyboard-shortcuts.md)。

## 脚注

```md
This is a footnote [^1].

[^1]: Here is the detail of the footnote.
```

## 上标和下标

```md
This is the 1^st^ superscript.

This is the H~2~O subscript.
```

## 标记

```md
Let's mark the ==word==.
```

## 警告框

用 `::: alert-xxx` 和 `:::` 包裹一个块，即可渲染出彩色提示框：

```md
::: alert-info

这是一个信息文本。

:::

::: alert-danger

这是一个危险文本。

:::
```

可用的一些形式如下：

```
alert-primary
alert-secondary
alert-success
alert-info
alert-warning
alert-danger
alert-light
alert-dark
```

## 内联 HTML

在 Markdown 力所不及之处，你可以直接插入原始 HTML——例如给文字上色：

```md
<font color="red">重要</font>

<mark>高亮</mark>
```

这与[片段](snippets.md)配合得很好：片段可以一键把选中文本包裹进这类标签。

**保护 Markdown 免受 XSS 攻击（Protect Markdown from XSS）**会过滤不安全的 HTML 与 URL；受保护笔记始终强制过滤。参见[设置](../customization/settings.md#markdown-safety-and-math)。

## 数学与图表

VNote 在美元符号分隔符内渲染数学公式：KaTeX（默认）和 MathJax 使用 LaTeX 语法，选择 **Typst** 后则使用 Typst 语法。`typst` 围栏标记独立于数学公式设置渲染。图表围栏包括 Mermaid、PlantUML（`puml`）、Graphviz（`dot`）、Flowchart.js（`flow`/`flowchart`）和 WaveDrom（`wavedrom`）。示例参见[数学与图表](math-and-diagrams.md)；原生 `.typst` 文档参见 [Typst](typst.md)。

## 换行和段落

如果需要换行，在当前行末尾添加两个空格，然后继续输入。VNote 提供快捷键 `Shift+Enter` 来辅助完成这一操作。

如果需要一个新的段落，先插入一个空行然后再输入新段落的文本。一般来说，应该在一个块元素（例如代码块、列表和块引用）后面插入一个空行来显式结束该元素。

## 渲染与扩展

VNote 4.12 在阅读模式、实时预览和 WebEngine 导出中使用 **cmark** 原生渲染 Markdown，复用当前编辑器的解析树，同时保留维基链接、任务列表、警告框和目录。[设置](../customization/settings.md)中仍可调整渲染选项；输出方式参见[导出](../productivity/export.md)。

4.12 移除了表情短代码和文本表情的自动展开：`:smile:` 或 `:-)` 等文本会保持原样。直接写入的 Unicode 字符不受影响。

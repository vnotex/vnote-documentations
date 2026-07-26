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

## 表格

```md
| col 1 | col 2 | col 3 |
| --- | --- | --- |
| cell1 | cell2 | cell3 |
| cell4 | cell5 | cell6 |
```

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
- 不推荐使用参考式的图片链接——VNote 不会预览这些图片。

你也可以直接粘贴图片，VNote 会把文件保存到笔记本中并替你写好链接。粘贴、本地存储与图床参见[图片与图床](images-and-image-host.md)。

```md
![替代文本](vx_assets/example.png)
```

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

这与[代码片段](snippets.md)配合得很好：片段可以一键把选中文本包裹进这类标签。

## 换行和段落

如果需要换行，在当前行末尾添加两个空格，然后继续输入。VNote 提供快捷键 `Shift+Enter` 来辅助完成这一操作。

如果需要一个新的段落，先插入一个空行然后再输入新段落的文本。一般来说，应该在一个块元素（例如代码块、列表和块引用）后面插入一个空行来显式结束该元素。

## 渲染与扩展

阅读模式将你的 Markdown 渲染为最终形式，也是[导出](../productivity/export.md)的基础。究竟启用哪些扩展——以及诸如表格风格或数学分隔符等细节——可在[设置](../customization/settings.md)中调整。如果某个元素没有按预期渲染，请检查那里的相关选项。

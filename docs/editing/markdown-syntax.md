# Markdown Syntax

VNote is designed around **Markdown**, a lightweight and easy-to-use syntax for writing, and its editor highlights this syntax in place as you type so your notes stay readable without a separate preview. There is no single standard for Markdown and many editors add their own extensions; VNote supports the widely-used basic syntax plus a few popular extensions. This page is a practical reference to what VNote understands. For the editing experience itself, see [Editor Basics](editor-basics.md).

## Headers

```md
# This is an <h1> tag
## This is an <h2> tag
###### This is an <h6> tag
```

- At least one space is needed after the `#`.
- A header should occupy one entire line.

Headers feed the interactive [outline](editor-basics.md), so use them to structure long notes.

## Emphasis

```md
*This text will be italic*
_This text will be italic_

**This text will be bold**
__This text will be bold__
```

- `*` is recommended in VNote.
- If the render fails, try adding a space before the first `*` and after the last `*`. The space is usually necessary if the surrounded text begins or ends with a full-width punctuation mark.

## Lists

### Unordered

```md
* Item 1  
This is a text under Item 1. Notice that there are two spaces at the end of the line above.
* Item 2
    * Item 2a
    * Item 2b
* Item 3

To end a list, there should be one empty line above.
```

### Ordered

```md
1. Item 1
1. Item 2  
Notice that the sequence number is irrelevant. Markdown renumbers the list automatically when rendering.
3. Item 3
    1. Item 3a
    2. Item 3b
4. Item 4
```

## Tables

```md
| col 1 | col 2 | col 3 |
| --- | --- | --- |
| cell1 | cell2 | cell3 |
| cell4 | cell5 | cell6 |
```

## Images and links

```md
![Image Alt Text](/url/to/image.png "Optional Title")

![Image Alt Text](/url/to/image.png "Image specified with width and height" =800x600)

![Image Alt Text](/url/to/image.png =800x600)

![Image Alt Text](/url/to/image.png "Image specified with width" =800x)

![Image Alt Text](/url/to/image.png "Image specified with height" =x600)

[Link Text](/url/of/the/link)
```

- The `=WIDTHxHEIGHT` suffix sets the rendered image size; omit either side to set only one dimension.
- Reference-style image links are not recommended — VNote will not preview those images.

You can also paste an image and VNote saves the file into the notebook and writes the link for you. See [Images & Image Host](images-and-image-host.md) for pasting, local storage, and image hosts.

```md
![alt text](vx_assets/example.png)
```

## Blockquotes

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

- A space is needed after the marker `>`.
- For consecutive quoted lines you can add `>` only on the first line.

## Fenced code blocks

Fence code with triple backticks (or tildes) and name the language for syntax highlighting:

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

- `lang` is optional; if not specified, VNote won't highlight the code. For the supported languages, see [Prism](https://prismjs.com/#supported-languages).
- It is good practice to add one empty line before the whole fenced code block.

## Inline code

```md
Here is an `inline code`.
```

To insert one `` ` ``, enclose it with two `` ` `` (`` `` ` `` ``). To insert two `` ` ``, use three `` ` ``.

## Strikethrough

```md
Here is a ~~text~~ with strikethrough.
```

## Task lists

```md
* [x] this is a complete item.
* [ ] this is an incomplete item.
```

## Footnotes

```md
This is a footnote [^1].

[^1]: Here is the detail of the footnote.
```

## Superscript and subscript

```md
This is the 1^st^ superscript.

This is the H~2~O subscript.
```

## Mark

```md
Let's mark the ==word==.
```

## Alert boxes

Wrap a block between `::: alert-xxx` and `:::` to render a colored callout:

```md
::: alert-info

This is an info text.

:::

::: alert-danger

This is a danger text.

:::
```

Available variants:

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

## Inline HTML

Where Markdown falls short, you can drop in raw HTML — for example to color text:

```md
<font color="red">important</font>

<mark>highlighted</mark>
```

This pairs well with [Snippets](snippets.md), which can wrap selected text in tags like these with a single keystroke.

## Math and diagrams

VNote renders LaTeX math (via MathJax) and several diagram languages — Mermaid, PlantUML (`puml`), Graphviz (`dot`), Flowchart.js (`flow`/`flowchart`), and WaveDrom (`wavedrom`) — from fenced code blocks. These have their own page — see [Math & Diagrams](math-and-diagrams.md).

## New lines and paragraphs

To start a new line, add two spaces at the end of the current line and continue typing. VNote provides `Shift+Enter` to do this for you.

To start a new paragraph, add an empty line and then continue. In general, add an empty line after a block element (such as a code block, list, or blockquote) to explicitly end it.

## Rendering and extensions

Read mode renders your Markdown to its final form and is the basis for [Export](../productivity/export.md). Exactly which extensions are enabled — and details such as the flavor of tables or math delimiters — can be adjusted in [Settings](../customization/settings.md). If an element doesn't render as expected, check the relevant option there.

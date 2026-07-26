# Markdown Syntax

VNote is designed around **Markdown**, and its editor highlights this syntax in place as you type so your notes stay readable without a separate preview. This page is a practical reference to the Markdown VNote understands, plus the extensions it adds. For the editing experience itself, see [Editor Basics](editor-basics.md).

## Basic syntax

```md
# Heading 1
## Heading 2
### Heading 3

Paragraphs are separated by a blank line.

**bold**, *italic*, ~~strikethrough~~, and `inline code`.

> A blockquote.

- Bulleted list item
- Another item
    - Nested item

1. Numbered list item
2. Second item

[A link](https://vnote.fun/)

---
```

Headings feed the interactive [outline](editor-basics.md), so use them to structure long notes.

## Code blocks

Fence code with triple backticks and name the language for syntax highlighting:

````md
```python
def hello():
    print("Hello, VNote")
```
````

## Tables

```md
| Column A | Column B |
| -------- | -------- |
| a1       | b1       |
| a2       | b2       |
```

## Task lists

```md
- [x] Done
- [ ] Not done yet
```

## Images

Insert images with standard Markdown, or simply paste them — VNote saves the file into the notebook and writes the link for you. See [Images & Image Host](images-and-image-host.md) for pasting, local storage, and image hosts.

```md
![alt text](vx_images/example.png)
```

## Math and diagrams

VNote renders LaTeX math and several diagram languages (PlantUML, Graphviz, Mermaid, and more) from fenced blocks. These have their own page — see [Math & Diagrams](math-and-diagrams.md).

## Inline HTML

Where Markdown falls short, you can drop in raw HTML — for example to color text:

```md
<font color="red">important</font>

<mark>highlighted</mark>
```

This pairs well with [Snippets](snippets.md), which can wrap selected text in tags like these with a single keystroke.

## Rendering and extensions

Read mode renders your Markdown to its final form and is the basis for [Export](../productivity/export.md). Exactly which extensions are enabled — and details such as the flavor of tables or math delimiters — can be adjusted in [Settings](../customization/settings.md). If an element doesn't render as expected, check the relevant option there.

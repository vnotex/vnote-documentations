# Markdown 语法

VNote 以 **Markdown** 为核心设计，其编辑器会在你输入时就地高亮这些语法，让笔记无需单独预览也保持易读。本页是 VNote 所能识别的 Markdown 以及它所增加扩展的实用参考。编辑体验本身参见[编辑器基础](editor-basics.md)。

## 基础语法

```md
# 一级标题
## 二级标题
### 三级标题

段落之间用空行分隔。

**加粗**、*斜体*、~~删除线~~，以及 `行内代码`。

> 引用块。

- 无序列表项
- 另一项
    - 嵌套项

1. 有序列表项
2. 第二项

[一个链接](https://vnote.fun/)

---
```

标题会汇入可交互的[大纲](editor-basics.md)，因此用它们来组织长笔记的结构。

## 代码块

用三个反引号围栏代码，并写明语言以获得语法高亮：

````md
```python
def hello():
    print("Hello, VNote")
```
````

## 表格

```md
| 列 A | 列 B |
| ---- | ---- |
| a1   | b1   |
| a2   | b2   |
```

## 任务列表

```md
- [x] 已完成
- [ ] 尚未完成
```

## 图片

用标准 Markdown 插入图片，或直接粘贴——VNote 会把文件保存到笔记本中并替你写好链接。粘贴、本地存储与图床参见[图片与图床](images-and-image-host.md)。

```md
![替代文本](vx_images/example.png)
```

## 数学与图表

VNote 能从围栏代码块渲染 LaTeX 数学公式和若干图表语言（PlantUML、Graphviz、Mermaid 等）。它们有专门的页面——参见[数学与图表](math-and-diagrams.md)。

## 内联 HTML

在 Markdown 力所不及之处，你可以直接插入原始 HTML——例如给文字上色：

```md
<font color="red">重要</font>

<mark>高亮</mark>
```

这与[代码片段](snippets.md)配合得很好：片段可以一键把选中文本包裹进这类标签。

## 渲染与扩展

阅读模式将你的 Markdown 渲染为最终形式，也是[导出](../productivity/export.md)的基础。究竟启用哪些扩展——以及诸如表格风格或数学分隔符等细节——可在[设置](../customization/settings.md)中调整。如果某个元素没有按预期渲染，请检查那里的相关选项。

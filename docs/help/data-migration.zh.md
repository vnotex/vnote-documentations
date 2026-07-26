# 数据迁移

由于 VNote 处理纯 Markdown 文件和图片，把内容迁入 VNote 通常只需先将其转为 Markdown 形式，再围绕它构建笔记本。VNote 没有为其他笔记应用提供内置导入器——开发资源有限——因此本页收集了有助于常见迁移的第三方工具。

!!! tip "贡献工具"
    如果你开发了有助于迁移到 VNote 的实用工具，欢迎联系我们，以便将其列在此处。

## 第一步：从你的文件构建笔记本

无论你从哪个工具导出，目标都是得到一个装着 Markdown 文件的文件夹。有了它之后，使用**新建笔记本**并将**类型**设为**原始笔记本（Raw notebook）**，即可将其变成笔记本而无需移动任何东西——参见[导入与迁移](../managing-notes/importing-migrating.md)。

## 第三方迁移工具

### ImageBedMoving

[ImageBedMoving](https://github.com/StarLeet/ImageBedMoving) 会把散落在各文件夹中被引用的图片移动到 VNote 的附件文件夹（默认为 `vx_assets`）。它通常在从外部文件夹构建笔记本**之后**使用，用于整理图片的存放位置。VNote 如何存储图片参见[图片与图床](../editing/images-and-image-host.md)。

## 从常见工具迁移

- **Typora、Obsidian 及其他 Markdown 编辑器**——它们本就存储纯 Markdown，因此用**新建笔记本 → 类型：原始笔记本**让 VNote 指向该文件夹即可。若图片散落各处，之后再运行 ImageBedMoving 之类的工具。
- **没有 Markdown 导出的应用**——先导出或转换为 Markdown（许多工具支持，或用 [Pandoc](https://pandoc.org/) 转换常见格式），然后从结果构建笔记本。

## 迁移 VNote 笔记本本身

在你自己的电脑之间迁移笔记本，与从其他应用导入不同——它只是复制一个文件夹并打开它。参见[笔记本同步](../managing-notes/notebook-sync.md)。

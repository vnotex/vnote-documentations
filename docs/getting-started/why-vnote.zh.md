# 为什么选择 VNote

VNote 是一款免费、开源、基于 Qt 的笔记应用，专注于 Markdown。它不只是一个编辑器：它将愉悦的编辑体验与强大的笔记管理结合在一起，并原生运行于 **Linux**、**Windows** 和 **macOS**。

本页介绍 VNote 的独特之处以及它适合哪些用户。如果你只想尽快开始记笔记，可直接跳转到[安装](installation.md)与[快速上手](quick-start.md)。

## VNote 是什么

VNote 将你的写作组织为**笔记本**。一个笔记本就是磁盘上的一个目录，包含笔记及其相关文件。普通 Markdown 和文本笔记是纯文本；可选的[加密笔记](../managing-notes/encrypted-notes.md)以受保护的格式保存正文，由 VNote 使用你的密码解锁。

本地文件由你掌控：可以备份、进行版本管理，或将完整笔记本迁移到另一台电脑。普通 Markdown 和文本笔记也可以用其他工具编辑。对于加密笔记，请同时保留笔记本元数据、密钥文件及密码；加密不会清除旧备份或 Git 历史中的明文。

## 为什么选择 VNote

<div class="grid cards" markdown>

-   :material-lock-outline:{ .lg .middle } __掌控你的数据__

    ---

    笔记是本地文件，并可选择加密正文。一个笔记本对应一个目录。可选择文件夹同步，或使用内置的 Git、WebDAV、坚果云同步。

-   :material-folder-multiple-outline:{ .lg .middle } __简单的笔记管理__

    ---

    自包含的笔记本、无限层级的文件夹以及纯粹的笔记。使用标签、快速访问和历史进行组织；直接浏览与编辑外部文件。

-   :material-language-markdown:{ .lg .middle } __愉悦的 Markdown 体验__

    ---

    原位与并排实时预览、语法高亮、可交互的大纲、高效的图片管理，以及数学公式与图表（PlantUML、Graphviz、Mermaid 等）。

-   :material-tune:{ .lg .middle } __为高级用户打造__

    ---

    Vi 模式、丰富的快捷键、标签页与窗口分屏、模糊搜索与跳转，以及通过主题、样式和行为进行的深度自定义。

</div>

## 掌控你的数据

隐私与长久可用是 VNote 设计的核心。

- **本地文件。** 普通 Markdown 和文本笔记无需 VNote 也可阅读；正文[加密](../managing-notes/encrypted-notes.md)是可选的例外。
- **一个笔记本，一个目录。** 请备份完整笔记本，包括元数据和加密密钥，而不只是笔记文件。
- **按你的方式同步。** 使用文件夹同步工具，或内置的 Git、WebDAV（包括 Nextcloud）、坚果云同步。配置步骤与服务差异参见[笔记本同步](../managing-notes/notebook-sync.md)。
- **掌控数据。** 普通笔记使用标准格式；若要在其他应用中编辑受保护笔记的内容，请先在 VNote 中解密。

## 简单且可扩展的笔记管理

VNote 从寥寥数篇笔记到庞大、深度嵌套的知识库都能胜任。

- 自包含的笔记本，支持**无限层级的文件夹**。
- 使用[标签](../managing-notes/tags.md)跨文件夹树组织笔记。
- 使用[快速访问与历史](../managing-notes/quick-access-history.md)回到你正在进行的工作。
- 导入并迁移已有笔记——参见[导入与迁移](../managing-notes/importing-migrating.md)。

## 愉悦的 Markdown 体验

写作是 VNote 投入精力最多的地方。

- 实时预览，支持**原位**与**并排**两种方式。
- 语法高亮与可交互的[大纲](../editing/editor-basics.md)。
- 高效的[图片管理](../editing/images-and-image-host.md)，包括图床。
- [数学公式与图表](../editing/math-and-diagrams.md)，支持 PlantUML、Graphviz、Mermaid 等。
- [片段](../editing/snippets.md)、[模板](../editing/templates.md)与[思维导图](../editing/mind-maps.md)，助力结构化写作。

## 为高级用户打造

- [Vi 模式](../editing/vi-mode.md)，提供模式化编辑。
- 标签页、窗口分屏以及丰富的[键盘快捷键](../customization/keyboard-shortcuts.md)。
- 跨笔记本的快速[搜索](../search/index.md)与跳转。
- 对主题、样式和行为的深度[自定义](../customization/index.md)。

## VNote 适合谁

如果你符合以下情况，VNote 会很适合你：

- 希望你的笔记是**你所拥有的纯文件**，而不是他人云端数据库中的条目。
- 大量记录 **Markdown** 笔记，并在意编辑体验。
- 维护**庞大或长期**的知识库，需要可扩展的文件夹、标签与搜索。
- 更愿意**自行选择同步方式**（文件夹同步、Git、WebDAV 或坚果云），而非由 VNote 托管的账户。
- 喜欢**以键盘为中心、可自定义**的工具——尤其是喜欢 Vi 的用户。

如果你需要实时多人协作，或需要完全托管的、基于账户的云服务，那么其他工具可能更适合你——VNote 专注于本地优先的单人笔记。

## 下一步

- 在你的平台上[安装 VNote](installation.md)。
- 跟随[快速上手](quick-start.md)创建你的第一个笔记本。
- 了解[仪表盘](dashboard.md)。

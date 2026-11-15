# VNote

**一个舒适的笔记平台。**

VNote 是一款免费、开源的笔记应用，致力于让记录、整理和探索笔记变得简单而愉快。

[开始使用](getting-started/index.md){ .md-button .md-button--primary }
[从 Gitee 下载 VNote](https://gitee.com/vnotex/vnote/releases){ .md-button }
[下载 VNote](https://github.com/vnotex/vnote/releases/latest){ .md-button }

![VNote 主窗口](assets/screenshots/main.webp){ .screenshot }

!!! info "适用于 VNote 4.14.4 的文档"
    文档已更新至最新稳定版 [VNote 4.14.4](https://github.com/vnotex/vnote/releases/tag/v4.14.4)，并涵盖 4.12.0 之后的近期稳定版本。升级前，请查看[平台要求](getting-started/installation.md#requirements)、[笔记本任务信任](productivity/tasks.md)及[加密笔记格式变化](managing-notes/encrypted-notes.md)。持续构建的行为可能与本指南不同。

## 近期版本 { #recent-releases }

| 稳定版本 | 主要变化与使用指南 |
| --- | --- |
| [4.14.4](https://github.com/vnotex/vnote/releases/tag/v4.14.4) · 2026-11-12 | 四种[标记隐藏预设](editing/editor-basics.md#markers-concealment)、三种 Markdown 编辑体验、用于[大纲思维导图](editing/mind-maps.md#outline-mind-maps)的 `Ctrl+G, F` 快捷键，以及仅有一个方案时直接创建[快速笔记](productivity/quick-note.md)。 |
| [4.14.2](https://github.com/vnotex/vnote/releases/tag/v4.14.2) · 2026-11-10 | [笔记本任务](productivity/tasks.md)的本机信任授权、Windows [阅读/编辑右键菜单](managing-notes/file-types.md)、经过认证的[增量更新](getting-started/installation.md#explicit-windows-updates)，以及[附加到主窗口](editing/editor-basics.md#detached-windows)。 |
| [4.14.1](https://github.com/vnotex/vnote/releases/tag/v4.14.1) · 2026-11-08 | 通过[大纲思维导图](editing/mind-maps.md#outline-mind-maps)编辑 Markdown 及具有可靠源映射的 Typst 标题，保存与撤销/重做均与源文档联动。 |
| [4.14.0](https://github.com/vnotex/vnote/releases/tag/v4.14.0) · 2026-11-05 | 按笔记本授权、需主动启用的 [HTTP API](productivity/http-api.md)、保留公式的 [HTML 转 Markdown 粘贴](editing/editor-basics.md#rich-text-and-html-paste)，以及[统一入口](search/united-entry.md)的文件名搜索与显式 `>` 命令。 |
| [4.13.0](https://github.com/vnotex/vnote/releases/tag/v4.13.0) · 2026-11-02 | 与源文档绑定的大纲及节点备注预览、原生 [Typst HTML/PDF 导出](editing/typst.md#pdf-output-and-printing)、[按源类型导出](productivity/export.md)，以及共享[导出样式](customization/themes-and-styles.md#applying-export-styles)。 |

4.14.3 已取消发布，其改动包含在 4.14.4 中。指南描述的是 4.14.4 的最终行为，而非已被替代的过渡设置；较早版本的截图会在说明中标明。

## 什么是 VNote？

无论是记录生活、构建个人知识库、整理学习笔记、撰写文档，还是梳理灵感与想法，VNote 都能为你提供一个舒适、统一的工作空间。

VNote 尤其擅长 **Markdown**，将强大的编辑体验与实用的笔记管理功能结合在一起。不过，VNote 并不只是 Markdown 编辑器：你还可以在同一个应用中使用**思维导图**、**Typst 文档**、**纯文本文件**等多种内容形式。

## 为什么选择 VNote

<div class="grid cards" markdown>

-   :material-pencil-outline:{ .lg .middle } __舒适地写作__

    ---

    无论是随手记下一个想法，还是撰写一篇长文，舒适的编辑体验都能让你把注意力放在内容本身。

-   :material-folder-multiple-outline:{ .lg .middle } __井井有条地管理笔记__

    ---

    通过笔记本和文件夹整理笔记。即使笔记越来越多，也能快速找到需要的内容。

-   :material-language-markdown:{ .lg .middle } __轻松使用 Markdown__

    ---

    自然地编写和预览 Markdown。无论你刚刚接触 Markdown，还是已经每天都在使用它，都能轻松上手。

-   :material-sitemap:{ .lg .middle } __用思维导图整理想法__

    ---

    直接创建和编辑思维导图，梳理想法之间的联系，让思路与知识结构一目了然。

-   :material-file-document-outline:{ .lg .middle } __不止于笔记__

    ---

    编辑纯文本文件，通过实时 PDF 预览撰写 Typst 文档，还可以直接阅读 PDF，无需频繁在多个应用之间切换。

-   :material-lock-outline:{ .lg .middle } __文件始终掌握在自己手中__

    ---

    内容保存在本地文件中，你可以使用熟悉的工具备份、移动和管理笔记本。

</div>

## 你的笔记，由你掌控

VNote 围绕本地文件构建，支持 Markdown、纯文本和 Typst 等开放格式，为你提供灵活的工作空间，让笔记始终由你掌控。

你可以从几篇 Markdown 笔记开始，逐渐建立自己的知识库；也可以用思维导图梳理想法，或者仅仅把 VNote 当作一个舒适、愉快的写作空间。

**VNote，为你的笔记、想法与知识提供一个长久的家。**

## 浏览文档

<div class="grid cards" markdown>

-   :material-rocket-launch-outline:{ .lg .middle } __快速开始__

    ---

    安装 VNote，记录第一篇笔记，并了解仪表盘。

    [:octicons-arrow-right-24: 快速开始](getting-started/index.md)

-   :material-notebook-outline:{ .lg .middle } __管理笔记__

    ---

    组织笔记本、文件夹和笔记；使用标签、同步、快速访问和历史记录。

    [:octicons-arrow-right-24: 管理笔记](managing-notes/index.md)

-   :material-pencil-outline:{ .lg .middle } __编辑__

    ---

    在 VNote 的各类编辑器中书写与排版——Markdown、Typst、数学公式、图表、片段、模板、思维导图和 Vi 模式。

    [:octicons-arrow-right-24: 编辑](editing/index.md)

-   :material-magnify:{ .lg .middle } __搜索__

    ---

    通过搜索面板和统一入口快速找到笔记。

    [:octicons-arrow-right-24: 搜索](search/index.md)

-   :material-lightning-bolt-outline:{ .lg .middle } __效率__

    ---

    使用任务自动化工作，并将笔记导出为其他格式。

    [:octicons-arrow-right-24: 效率](productivity/index.md)

-   :material-cog-outline:{ .lg .middle } __自定义__

    ---

    配置设置，应用主题与样式，并自定义键盘快捷键。

    [:octicons-arrow-right-24: 自定义](customization/index.md)

</div>

## 开源和自由

- 遵从 [GNU LGPLv3](https://opensource.org/licenses/LGPL-3.0) 开源协议。
- 由 Qt 和 C++ 提供强劲性能。
- 支持 Linux、Windows 和 macOS。

## 参与其中

- 在 [GitHub](https://github.com/vnotex/vnote) 上关注并 Star VNote。
- 通过 [GitHub Issues](https://github.com/vnotex/vnote/issues) 反馈问题。

!!! tip "需要帮助？"
    请查阅[帮助](help/index.md)章节，获取常见问题解答和数据迁移指南。

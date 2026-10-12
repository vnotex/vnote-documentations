# 常见问题

这里解答常见问题并给出人们最常遇到问题的修复方法。如果这里没有你的问题，请查阅文档的其余部分或项目的 [GitHub issues](https://github.com/vnotex/vnote/issues)。

## 如何指定自定义的 MathJax 脚本？ { #custom-mathjax }

VNote 现在默认使用内置、可离线工作的 **KaTeX**。若要使用 MathJax，请在**设置 → Markdown 编辑器 → 数学公式渲染器（Math renderer）**中选择它，再在**覆盖 MathJax 脚本（Override MathJax script）**中填写脚本 URL（也可以是本地文件 URL）。留空则使用默认脚本；无需再复制并修改 `web/js/mathjax.js`。

完整步骤和示例参见[自定义 MathJax](../editing/math-and-diagrams.md#customizing-mathjax)。

## VNote 在版本更新后崩溃

当更新跨越多个版本、旧配置不再兼容时，常会发生这种情况。打开你的**用户**配置文件夹，删除 `vnotex.json`，然后重启 VNote。该文件夹的位置参见[设置](../customization/settings.md)。

## 界面卡死、编辑模式下光标不可见，或打开笔记时 VNote 崩溃

在 **Windows** 上，这三种症状通常由显卡驱动引起。依次尝试以下步骤，每一步后重启 VNote 检查是否有效：

1. 更新显卡驱动。
2. 设置 VNote 使用集成显卡运行。
3. 若无效，在**设置**中逐一尝试各个 `OpenGL` 值。
4. 确保 VNote 的可执行文件夹位于 `C:` 盘。

## 我的笔记存放在哪里？

存放在你放置它们的地方。每个笔记本都有一个称为*笔记本根文件夹*的目录。普通 Markdown 笔记仍是纯文本文件，独立图片保存在资源文件夹中（默认为 `vx_assets`），索引和缓存与正文分开存储。捆绑笔记本中可选的[加密笔记](../managing-notes/encrypted-notes.md)是例外：其正文不是能供外部编辑器直接处理的明文文件。参见[笔记本、文件夹与笔记](../managing-notes/notebooks-folders-notes.md)。

## 如何在多台设备间同步笔记？

捆绑笔记本支持内置的 **Git**、**WebDAV**（包括 Nextcloud）和**坚果云（WebDAV）**同步。Dropbox、OneDrive 等外部文件夹同步工具仍可作为替代方案；不要让多种同步方式同时修改同一个笔记本。参见[笔记本同步](../managing-notes/notebook-sync.md)。

## 我能便携地使用 VNote（从 U 盘）吗？

可以。按[让 VNote 便携化](../customization/settings.md#make-vnote-portable)所述，把配置与可执行文件放在一起。

## 如何导入我已有的 Markdown 文件？

创建一个**捆绑笔记本**并把你的文件夹导入其中——参见[导入与迁移](../managing-notes/importing-migrating.md)。如果你更希望完全按原样接纳现有文件夹，可以用**新建笔记本 → 类型：原始笔记本**打开它，它会就地浏览该文件夹，但没有标签、附件和回收站。从其他应用迁移参见[数据迁移](data-migration.md)。

## 为什么我的笔记在一个独立窗口中打开了？

那个窗口是**分离视图**。[快速笔记](../productivity/quick-note.md)方案可以设置为在其中打开笔记。当你对标签页使用**分离（Detach）**、在笔记本浏览器中使用**以分离方式打开（Open as Detached）**，或使用[命令行](../getting-started/command-line.md)选项 `--detached-view` 时，就会出现它。关闭该窗口或把它的标签页拖回，即可让笔记回到主窗口——参见[编辑器基础](../editing/editor-basics.md)。

## VNote 会自动更新吗？

不会在未经你操作的情况下更新。普通检查仍然只查询新版本；在 Windows 上，启动时的更新通知还提供**立即更新（Update Now）**，只有你主动选择后才会启动外部更新器。其他平台采用手动更新。参见[检查更新](../getting-started/installation.md)。

## 捆绑笔记本和原始笔记本有什么区别？

捆绑笔记本会在其根文件夹下维护一份索引，正是这份索引让标签、附件、回收站、内置的 Git/WebDAV/坚果云同步以及可选的笔记正文加密成为可能。原始笔记本没有索引——它像文件浏览器一样就地浏览一个文件夹——因此这些功能都不可用。请优先选择捆绑笔记本；只有当现有文件夹必须按原样被接纳，或者由 VNote 之外的东西管理时，才选择原始笔记本。参见[笔记本、文件夹与笔记](../managing-notes/notebooks-folders-notes.md#which-type-should-i-use)。

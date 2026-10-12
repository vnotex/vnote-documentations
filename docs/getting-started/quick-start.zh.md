# 快速上手

本页带你在几分钟内从全新安装走到第一篇笔记。如果你尚未安装 VNote，请参见[安装](installation.md)。

## 试用示例笔记本 { #try-the-demo-notebook }

想先探索一个现成的笔记本？[文档仓库](https://github.com/vnotex/vnote-documentations)中的 [`demo-notebook/`](https://github.com/vnotex/vnote-documentations/tree/main/demo-notebook) 提供成对的英文和中文示例，涵盖 Markdown、任务清单、表格、代码和笔记间链接。

1. 克隆仓库，或在 GitHub 上选择 **Code → Download ZIP** 并解压。
2. 尝试编辑之前，将 `demo-notebook/` 复制到可写位置；VNote 中的编辑会修改磁盘上的文件。
3. 在 VNote 的**笔记本**面板中打开三点菜单，选择**打开文件夹为原生笔记本（Open Folder As Raw Notebook）**，然后选中复制后的 `demo-notebook` 文件夹，而非仓库根目录。
4. 打开 `Welcome.zh.md`（英文示例为 `Welcome.md`），然后通过链接访问 **Markdown 导览**和 **Projects** 文件夹中的**发布计划**。

此操作将文件夹作为**原始笔记本**就地打开，不会复制或迁移文件。不要使用**打开笔记本（Open Notebook）**，该操作需要捆绑笔记本。`.zh.md` 文件是与英文笔记并列的中文示例，而非语言包。如需标签、附件、回收站、加密或内置同步，请改用捆绑笔记本；参见[导入与迁移](../managing-notes/importing-migrating.md)。

![在 VNote 中打开的示例笔记本：阅读模式下的中文欢迎页和左侧笔记树](../assets/screenshots/demo-read.webp){ .screenshot loading=lazy }

*截图来自 Windows 上的 VNote 4.9.1，使用英文界面和仓库中的中文示例笔记。*

## 1. 创建笔记本

VNote 将笔记组织为**笔记本**。一个笔记本就是磁盘上的一个目录，因此第一步是选择笔记的存放位置。

1. 打开 VNote。在左侧打开笔记本选择器并选择**新建笔记本**。
2. 选择一个**空**目录作为*笔记本根文件夹*。在默认的**捆绑笔记本（Bundled notebook）**类型下，这个笔记本中的一切——笔记、图片和配置——都存放在这里。
3. 为笔记本取个名字，并可选填写描述，然后确认。

!!! tip "已经有 Markdown 文件了？"
    照常创建笔记本，然后从工具栏的**新建**菜单中使用**导入文件夹（Import Folder）**把你已有的目录带进来。如果你更希望完全按原样接纳该文件夹，可将笔记本**类型**设为**原始笔记本（Raw notebook）**以就地浏览它——代价是失去标签、附件和回收站。参见[导入与迁移](../managing-notes/importing-migrating.md)。

## 2. 创建文件夹（可选）

笔记本可以包含**文件夹**，并支持任意层级的嵌套。在导航面板中右键点击笔记本并选择**新建文件夹**，即可将相关笔记归为一组。你也可以跳过这一步，之后再添加文件夹。

## 3. 创建你的第一篇笔记

1. 选中笔记应存放的笔记本或文件夹。
2. 点击**新建笔记**（或按菜单中显示的快捷键）。
3. 输入名称，例如 `welcome.md`。`.md` 后缀会创建一篇 Markdown 笔记。
4. 笔记在编辑器中打开，你可以开始输入了。

## 4. 编写与预览

VNote 为 Markdown 提供**实时体验**：随着你的输入，标题、列表和强调会就地高亮。你也可以打开**并排预览**或切换到**阅读模式**查看完整渲染结果。编辑模式与大纲详见[编辑器基础](../editing/editor-basics.md)。

## 5. 在磁盘上找到你的笔记

在文件管理器中打开笔记本根文件夹。刚创建的普通笔记是一个纯 `.md` 文件。以文件方式插入的图片单独保存（默认位于 `vx_assets` 中），Base64 图片则嵌入笔记正文。请备份完整笔记本，或配置[笔记本同步](../managing-notes/notebook-sync.md)。如果之后启用[笔记正文加密](../managing-notes/encrypted-notes.md)，还需保留密钥文件和密码：此次转换不会加密独立资源文件、旧备份或 Git 历史。

## 下一步

- 了解[仪表盘](dashboard.md)与主界面。
- 通过[笔记本、文件夹与笔记](../managing-notes/notebooks-folders-notes.md)和[标签](../managing-notes/tags.md)进行组织。
- 探索[编辑](../editing/index.md)功能，从数学与图表到片段与模板。

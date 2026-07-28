# 设置

VNote 的大部分行为都可以调整，既可以通过**设置**对话框，也可以直接编辑配置文件。本页说明 VNote 的配置是如何分层的、文件位于何处，以及如何让 VNote 便携化。

## 设置对话框

从工具栏或菜单打开**设置**，即可更改常用选项——外观与[主题](themes-and-styles.md)、编辑器行为、[Vi 模式](../editing/vi-mode.md)、阅读/渲染选项、[图床](../editing/images-and-image-host.md)等。对话框中未暴露的项，可以编辑下文所述的配置文件。

![设置对话框](../assets/screenshots/settings.webp){ .screenshot loading=lazy }

## 配置的层级

VNote 的配置是分层的，按顺序应用：

- **默认配置**——应用内置的默认值。它们内建于程序之中，磁盘上没有可供复制的文件。若要自定义某个值，在你的*用户配置*文件中设置它，它会覆盖默认值。
- **用户配置**——你在用户配置文件夹中的主文件 `vnotex.json` 里的覆盖设置。这里的任何内容都优先于默认值。
- **会话配置**——会话状态，例如笔记本列表和主窗口的几何布局。它是 `session.json` 文件。VNote 在运行期间会持续写入它，并在关闭时刷新落盘，因此手动编辑前请先关闭 VNote。

## 配置文件夹里有什么

配置文件夹包含若干文件夹和主文件：

```
.
├── dicts               （拼写检查词典）
├── syntax-highlighting （文本编辑器的 Kate 语法高亮文件）
├── tasks               （任务定义；参见「任务」）
├── themes              （VNote 主题）
├── web                 （阅读模式使用的资源）
└── vnotex.json         （主配置文件）
```

要自定义 `vnotex.json` 的字段，添加或编辑你需要的键即可——VNote 会把你的文件合并到内置默认值之上。你在别处会看到引用的按功能划分的相关文件夹包括 `tasks`（参见[任务](../productivity/tasks.md)）和 `templates`（参见[模板](../editing/templates.md)）。

## 让 VNote 便携化 { #make-vnote-portable }

你可以把配置与可执行文件放在一起，让整套环境一同迁移——例如放在 U 盘上：

1. 先关闭 VNote。
2. 在可执行文件（如 `vnote.exe`）旁边创建一个名为 `config` 的文件夹。
3. 在其中，VNote 会使用两个子文件夹：`app`（应用设置，包含 `vnotex.json`）和 `local`（会话与缓存，包含 `session.json`）。VNote 会在首次运行时创建它们。

当启动时可执行文件旁存在 `config` 文件夹，VNote 就会在那里读写配置，而不再使用系统级位置。

## 相关自定义

- [主题与样式](themes-and-styles.md)——更改界面、编辑器和阅读模式的外观。
- [键盘快捷键](keyboard-shortcuts.md)——重新映射操作，包括[统一入口](../search/united-entry.md)。
- 如果 VNote 在版本更新后崩溃，从用户配置文件夹删除 `vnotex.json` 是常见的修复方法——参见[常见问题](../help/faq.md)。

# 安装

VNote 提供 **Linux**、**Windows** 和 **macOS** 版本。它免费且开源，无需注册账户——下载、运行，即可开始记笔记。

## 下载

各平台的独立安装包都发布在项目的发布页面：

- [VNote 官网下载](https://vnote.fun/)
- [GitHub Releases](https://github.com/vnotex/vnote/releases)

日常使用推荐**稳定版**。如果你想在正式发布前体验最新功能，可以尝试 `master` 分支的最新持续构建，但需要承担一定的稳定性风险。

## Windows

1. 从发布页面下载 Windows 安装包（`.zip` 压缩包或安装程序）。
2. 如果下载的是压缩包，将其解压到一个你有写入权限的文件夹，然后运行 `VNote.exe`。
3. 如果下载的是安装程序，运行它并按提示操作。

!!! tip "将 VNote 放在受保护目录之外"
    在 Windows 上，建议使用 `C:\Tools\VNote` 之类的位置，而不是 `C:\Program Files`。这样可以避免权限问题，在极少数情况下还能规避显卡驱动导致的崩溃。若 VNote 无法启动，请参见[常见问题](../help/faq.md)。

## macOS

1. 下载 `.dmg` 安装包，打开后将 **VNote** 拖入 `Applications` 文件夹。
2. 首次启动时，macOS 可能提示该应用来自身份不明的开发者。右键点击应用并选择**打开**，然后确认。

VNote 也可通过 **Homebrew Cask** 安装：

```bash
brew install --cask vnote
```

## Linux

VNote 以 **AppImage** 形式提供，以获得广泛的兼容性：

1. 下载 `.AppImage` 文件。
2. 赋予可执行权限：`chmod +x VNote-*.AppImage`。
3. 运行：`./VNote-*.AppImage`。

部分发行版有社区维护的软件包（例如 Arch Linux 的 **AUR** 中就有 VNote）。可用性与更新及时程度因发行版而异。

## 便携式安装

你可以把 VNote 的配置与可执行文件放在一起，让整套环境可以放在 U 盘或同步文件夹中。步骤参见[将 VNote 便携化](../customization/settings.md#make-vnote-portable)。

## 下一步

- 跟随[快速上手](quick-start.md)创建你的第一个笔记本和笔记。
- 熟悉[仪表盘](dashboard.md)与主界面。

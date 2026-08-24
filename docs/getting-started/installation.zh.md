# 安装

VNote 提供 **Linux**、**Windows** 和 **macOS** 版本。它免费且开源，无需注册账户——下载、运行，即可开始记笔记。

## 下载

各平台的独立安装包都发布在项目的发布页面：

- [GitHub Releases](https://github.com/vnotex/vnote/releases)
- [Gitee Releases](https://gitee.com/vnotex/vnote/releases)

日常使用推荐**稳定版**。如果你想在正式发布前体验最新功能，可以尝试 `master` 分支的最新持续构建，但需要承担一定的稳定性风险。

## 系统要求

VNote 基于 Qt 6 构建，提供以下平台的安装包：

| 安装包 | 说明 |
|--------|------|
| **Windows x64** | 常规 Windows 版本，基于 Qt 6.10.3 构建。需要 Windows 10 或更高版本。 |
| **Windows 7（`win64-windows7`）** | 面向旧版 Windows 的独立版本，基于 Qt 5.15 构建。注意事项见下文。 |
| **Linux x64** | 以 AppImage 形式发布，可在大多数现代发行版上运行。 |
| **macOS** | 通用（universal）版本，可在 Intel 与 Apple Silicon 芯片的 Mac 上原生运行。需要 macOS 10.15 或更高版本。 |

除非你使用的是 Windows 7 或 8，否则请选择对应平台的常规安装包。

## Windows

1. 从发布页面下载 Windows 安装包（`.zip` 压缩包或安装程序）。
2. 如果下载的是压缩包，将其解压到任意位置，然后运行 `VNote.exe`。安装目录无需可写，放在 `C:\Program Files` 也没有问题。
3. 如果下载的是安装程序，运行它并按提示操作。

如果你使用 [Scoop](https://scoop.sh/)，VNote 已收录在 `extras` bucket 中：

```powershell
scoop bucket add extras
scoop install extras/vnote
```

!!! warning "Windows 7 版本存在限制"
    `win64-windows7` 安装包基于 Qt 5.15 构建，无法提供 Qt 6 版本的全部功能。内置的 [PDF 阅读器](../managing-notes/pdf-viewer.md)在该版本中无法工作——请改用外部应用打开 PDF。该安装包自带 OpenSSL 1.1.1w；早期的 Windows 7 版本搜索时完全返回不到结果，网络操作也会以 “TLS initialization failed” 失败，这个 OpenSSL 修复了上述问题。请勿把随包附带的文件分开存放。

## macOS

1. 下载 `.dmg` 安装包，打开后将 **VNote** 拖入 `Applications` 文件夹。
2. 首次启动时，macOS 可能提示该应用来自身份不明的开发者。右键点击应用并选择**打开**，然后确认。

此外也可能有社区维护的 **Homebrew Cask** 可供使用：

```bash
brew install --cask vnote
```

VNote 会注册一个系统**服务**：在任意应用中选中文本，然后选择**服务 → Create Note in VNote**，即可把它记成一篇笔记。macOS 可能需要先启动一次 VNote——偶尔还需要注销并重新登录——该菜单项才会出现。

## Linux

VNote 以 **AppImage** 形式提供，以获得广泛的兼容性：

1. 下载 `.AppImage` 文件。
2. 赋予可执行权限：`chmod +x VNote-*.AppImage`。
3. 运行：`./VNote-*.AppImage`。

部分发行版有社区维护的软件包（例如 Arch Linux 的 **AUR** 中就有 VNote）。可用性与更新及时程度因发行版而异。

## 检查更新

VNote 只会*检查*是否有新版本。它不下载、不安装任何东西，也绝不会修改自己的安装目录——新版本需要你自行下载并安装，方式与当前版本相同。

**手动检查**：在主窗口菜单中选择**检查更新**。如果存在新版本，对话框会提供**打开发布页面**、**跳过此版本**和**稍后**三个选项；否则它只会告诉你 VNote 已是最新版本。

**自动检查**：**设置 → 常规 → 启动时检查更新**会在 VNote 启动时执行同样的检查，每 24 小时最多一次，并且只在确实有更新时才提示——此时会出现一条带**查看发布**操作的通知。新配置默认启用该选项。

**更新源**：同样位于**设置 → 常规**，用于选择向 GitHub 还是 Gitee 查询。新安装默认使用 **Gitee**；已有配置则保持原有设置不变。

!!! note "残留的更新目录"
    早期某个版本曾短暂内置过自动更新器，它可能在 `VNote.exe` 旁留下 `.vnote-old` 或 `.vnote-update` 文件夹。VNote 已不再创建或读取它们，可以放心删除。

## 便携式安装

你可以把 VNote 的配置与可执行文件放在一起，让整套环境可以放在 U 盘或同步文件夹中。步骤参见[将 VNote 便携化](../customization/settings.md#make-vnote-portable)。

## 下一步

- 跟随[快速上手](quick-start.md)创建你的第一个笔记本和笔记。
- 熟悉[仪表盘](dashboard.md)与主界面。
- 若你从终端或脚本启动 VNote，请参阅[命令行](command-line.md)选项。

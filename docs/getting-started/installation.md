# Installation

VNote is distributed for **Linux**, **Windows**, and **macOS**. It is free and open source, and there is no account to create — download it, run it, and start taking notes.

## Download

Standalone packages for every platform are published on the project's release pages:

- [GitHub Releases](https://github.com/vnotex/vnote/releases)
- [Gitee Releases](https://gitee.com/vnotex/vnote/releases)

We recommend the **stable releases** for everyday use. If you want the newest features before they are released, you can try the latest continuous build from the `master` branch, at the cost of some stability.

## Requirements

VNote is built with Qt 6 and published for these platforms:

| Package | Notes |
|---------|-------|
| **Windows x64** | The regular Windows build, made with Qt 6.10.3. Requires Windows 10 or newer. |
| **Windows 7 (`win64-windows7`)** | A separate build against Qt 5.15 for older Windows versions. See the caveats below. |
| **Linux x64** | AppImage built on Ubuntu 22.04; compatibility depends on the distribution and its system libraries. |
| **macOS** | Universal build for Intel and Apple Silicon. The regular package requires macOS 13 or newer. |
| **macOS 12 (`-macos12`)** | Separate universal package targeting macOS 12.1 or newer. |

Pick the regular package for your platform unless you need the Windows 7/8 or macOS 12 variant. The [v4.9.1 release](https://github.com/vnotex/vnote/releases/tag/v4.9.1) includes both macOS variants.

## Windows

1. Download the Windows package (a `.zip` archive or an installer) from the releases page.
2. If you downloaded the archive, extract it anywhere and run `VNote.exe`. The installation folder does not need to be writable for normal use, so `C:\Program Files` is fine; updating a protected installation requires a manual update.
3. If you downloaded an installer, run it and follow the prompts.

If you use [Scoop](https://scoop.sh/), VNote is available in the `extras` bucket:

```powershell
scoop bucket add extras
scoop install extras/vnote
```

!!! warning "The Windows 7 build has limitations"
    The `win64-windows7` package is built against Qt 5.15 and cannot offer everything the Qt 6 build does. The built-in [PDF viewer](../managing-notes/pdf-viewer.md) is disabled there because pdf.js 6 requires a newer web engine; VNote opens PDFs with the configured external application or the system default instead. This package ships its own OpenSSL 1.1.1w; earlier Windows 7 builds returned no search results at all and failed network operations with "TLS initialization failed", which that OpenSSL fixes. Keep the files that come with the package together.

## macOS

1. Download the `.dmg` for your macOS version: the regular universal package for macOS 13+, or the `-macos12` package for macOS 12.1+. Open it and drag **VNote** into your `Applications` folder.
2. The first time you launch it, macOS may warn that the app is from an unidentified developer. Right-click the app and choose **Open**, then confirm.

A community-maintained **Homebrew Cask** may also be available:

```bash
brew install --cask vnote
```

VNote registers a system **Service**: select text in any application and choose **Services → Create Note in VNote** to capture it as a note. macOS may need one launch of VNote — and occasionally a log out and back in — before the entry appears in the menu.

## Linux

VNote is provided as an **AppImage**, built on Ubuntu 22.04:

1. Download the `.AppImage` file.
2. Make it executable: `chmod +x VNote-*.AppImage`.
3. Run it: `./VNote-*.AppImage`.

Community-maintained packages exist for some distributions (for example, VNote is available in the **AUR** on Arch Linux). Availability and freshness vary by distribution.

## Checking for updates

Ordinary update checks only look for a newer release; they do not download or install it. You can always update manually from the release page. On Windows, a separate, explicit **Update Now** action is also available in the startup update notification.

**Manually**: choose **Settings → Check for Updates** in the main window. If a newer release exists, a dialog offers **Open Release Page**, **Skip This Version** and **Later**. Otherwise it simply reports that VNote is up to date.

**Automatically**: **Settings → General → Check for updates on start** performs the same check when VNote starts, at most once every 24 hours, and only says something when an update actually exists — a notification appears with a **Check Release** action. The option is enabled by default for new configurations.

**Update source**: also under **Settings → General**, this chooses whether the check queries GitHub or Gitee. New installations default to **Gitee**; an existing configuration keeps whatever it already had.

### Explicit Windows updates

On Windows, choose **Update Now** in the startup update notification to launch the external updater. It downloads and verifies a signed full update package while VNote stays open, then asks VNote to save and close. Installation and reopening proceed only after shutdown is accepted; cancelling a close/save prompt cancels that handoff.

The updater preserves portable `config` data and files not owned by the application package, and retains a recovery backup of the previous installation. Protected or non-writable installations receive manual-update guidance through **Check Release** rather than an elevation prompt. macOS and Linux updates remain manual.

!!! warning "Keep recovery data until it is no longer needed"
    Do not blindly delete folders with updater-related names such as `.vnote-old` or `.vnote-update`. Keep the recovery backup reported by the updater, especially after an interrupted or failed update, and follow its recovery instructions. If installation succeeds but reopening fails, open `VNote.exe` manually from the installation folder.

## Portable installation

You can bundle VNote's configuration next to the executable so the whole setup can live on a USB drive or a synced folder. See [Make VNote portable](../customization/settings.md#make-vnote-portable) for the steps.

## Next steps

- Follow the [Quick Start](quick-start.md) to create your first notebook and note.
- Get familiar with the [Dashboard](dashboard.md) and the main interface.
- See the [Command Line](command-line.md) options if you launch VNote from a terminal or a script.

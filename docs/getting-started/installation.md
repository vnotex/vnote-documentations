# Installation

VNote is distributed for **Linux**, **Windows**, and **macOS**. It is free and open source, and there is no account to create — download it, run it, and start taking notes.

## Download

Standalone packages for every platform are published on the project's release pages:

- [GitHub Releases](https://github.com/vnotex/vnote/releases)
- [Gitee Releases](https://gitee.com/vnotex/vnote/releases)

We recommend the latest stable release, [**v4.14.4**](https://github.com/vnotex/vnote/releases/tag/v4.14.4), for everyday use. If you want the newest features before they are released, you can try the latest continuous build from the `master` branch, at the cost of some stability.

## Requirements

VNote is built with Qt 6 and published for these platforms:

| Package | Notes |
|---------|-------|
| **Windows x64** | The v4.14.4 package uses Qt 6.10.3. Use a supported Windows 10 or Windows 11 release; see the runtime requirements below. |
| **Linux x64** | AppImage built on Ubuntu 22.04; compatibility depends on the distribution and its system libraries. |
| **macOS** | Universal build for Intel and Apple Silicon. The regular package requires macOS 13 or newer. |
| **macOS 12 (`-macos12`)** | Separate universal package targeting macOS 12.1 or newer. |

Pick the regular package for your platform unless you need the macOS 12 variant. The [v4.14.4 release](https://github.com/vnotex/vnote/releases/tag/v4.14.4) provides both macOS variants; its tagged [macOS](https://github.com/vnotex/vnote/blob/v4.14.4/.github/workflows/ci-macos.yml) and [Linux](https://github.com/vnotex/vnote/blob/v4.14.4/.github/workflows/ci-linux.yml) build configurations specify the targets above.

VNote 4.11 and later no longer support Windows 7 or older Windows 10 releases. The [Windows build configuration](https://github.com/vnotex/vnote/blob/v4.14.4/.github/workflows/ci-win.yml) uses Qt 6.10.3; [Qt 6.10's supported platforms](https://doc.qt.io/qt-6.10/supported-platforms.html#windows) list Windows 10 version 1809 or later and Windows 11 for x64. This is Qt's baseline, not a separately tested VNote minimum: the [VNote 4.11 release notes](https://github.com/vnotex/vnote/releases/tag/v4.11.0) do not name an exact Windows 10 version. There is no current Windows 7/8 package.

## Windows

1. Download `VNote-4.14.4-win64.zip` from the stable release page. The `.delta.zip` and manifest/signature files are updater assets, not standalone installations.
2. Extract the archive and run `VNote.exe`. The installation folder does not need to be writable for normal use, so `C:\Program Files` is fine; updating a protected installation requires a manual update.

If you use [Scoop](https://scoop.sh/), VNote is available in the `extras` bucket:

```powershell
scoop bucket add extras
scoop install extras/vnote
```

### Windows context menus { #windows-context-menus }

In **Settings → File Associations → System Context Menu**, choose **Add to Context Menu** to register **Read in VNote** and **Edit in VNote** for the applied built-in file suffixes. Apply suffix changes first, then add again to reconcile the registered extensions. **Read in VNote** opens a detached window in read mode; **Edit in VNote** opens in the main window in edit mode. These modes are preserved when forwarding to an already-running instance. Registration is per-user and does not require administrator privileges; **Remove from Context Menu** removes it, and legacy all-files entries are cleaned up. See the [4.14.2 release notes](https://github.com/vnotex/vnote/releases/tag/v4.14.2) and equivalent [command-line options](command-line.md#read-and-edit-modes).

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

On Windows, choose **Update Now** in the startup update notification to launch the external updater. When eligible, it downloads an authenticated delta and reconstructs and verifies the complete target payload while VNote stays open, before asking VNote to save and close. Otherwise it uses the signed full package. Installation and reopening proceed only after shutdown is accepted; cancelling a close/save prompt cancels that handoff.

Full-package fallback is limited to safe cases, such as an unavailable delta or installed files that cannot supply the required reusable bytes. Signature, integrity, unsafe-path, and other security failures stop the attempt instead of bypassing validation; cancellation and general network failures are not a reason to silently fall back. See the [v4.14.4 updater](https://github.com/vnotex/vnote/blob/v4.14.4/scripts/update-vnote.ps1).

The updater preserves portable `config` data and files not owned by the application package, and retains a recovery backup of the previous installation. Protected or non-writable installations receive manual-update guidance through **Check Release** rather than an elevation prompt. macOS and Linux updates remain manual.

!!! warning "Keep recovery data until it is no longer needed"
    Do not blindly delete folders with updater-related names such as `.vnote-old` or `.vnote-update`. Keep the recovery backup reported by the updater, especially after an interrupted or failed update, and follow its recovery instructions. If installation succeeds but reopening fails, open `VNote.exe` manually from the installation folder.

## Portable installation

You can bundle VNote's configuration next to the executable so the whole setup can live on a USB drive or a synced folder. See [Make VNote portable](../customization/settings.md#make-vnote-portable) for the steps.

## Next steps

- Follow the [Quick Start](quick-start.md) to create your first notebook and note.
- Get familiar with the [Dashboard](dashboard.md) and the main interface.
- See the [Command Line](command-line.md) options if you launch VNote from a terminal or a script.

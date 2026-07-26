# Installation

VNote is distributed for **Linux**, **Windows**, and **macOS**. It is free and open source, and there is no account to create — download it, run it, and start taking notes.

## Download

Standalone packages for every platform are published on the project's release pages:

- [Downloads on the VNote website](https://vnote.fun/)
- [GitHub Releases](https://github.com/vnotex/vnote/releases)

We recommend the **stable releases** for everyday use. If you want the newest features before they are released, you can try the latest continuous build from the `master` branch, at the cost of some stability.

## Windows

1. Download the Windows package (a `.zip` archive or an installer) from the releases page.
2. If you downloaded the archive, extract it to a folder you can write to, then run `VNote.exe`.
3. If you downloaded an installer, run it and follow the prompts.

!!! tip "Keep VNote outside protected folders"
    On Windows, prefer a location like `C:\Tools\VNote` over `C:\Program Files`. This avoids permission issues and, in rare cases, works around display-driver crashes. See the [FAQ](../help/faq.md) if VNote fails to start.

## macOS

1. Download the `.dmg` package, open it, and drag **VNote** into your `Applications` folder.
2. The first time you launch it, macOS may warn that the app is from an unidentified developer. Right-click the app and choose **Open**, then confirm.

VNote is also available through **Homebrew Cask**:

```bash
brew install --cask vnote
```

## Linux

VNote is provided as an **AppImage** for broad compatibility:

1. Download the `.AppImage` file.
2. Make it executable: `chmod +x VNote-*.AppImage`.
3. Run it: `./VNote-*.AppImage`.

Community-maintained packages exist for some distributions (for example, VNote is available in the **AUR** on Arch Linux). Availability and freshness vary by distribution.

## Portable installation

You can bundle VNote's configuration next to the executable so the whole setup can live on a USB drive or a synced folder. See [Make VNote portable](../customization/settings.md#make-vnote-portable) for the steps.

## Next steps

- Follow the [Quick Start](quick-start.md) to create your first notebook and note.
- Get familiar with the [Dashboard](dashboard.md) and the main interface.

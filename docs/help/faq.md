# FAQ

Answers to common questions and fixes for issues people hit most often. If your question isn't here, check the rest of the docs or the project's [GitHub issues](https://github.com/vnotex/vnote/issues).

## How do I specify a custom MathJax script? { #custom-mathjax }

VNote now uses bundled, offline **KaTeX** by default. To use MathJax, select it under **Settings → Markdown Editor → Math renderer**, then set **Override MathJax script** to your script URL (including a local file URL if needed). Leave the override empty to use the default script; you no longer need to copy and edit `web/js/mathjax.js`.

For the full procedure and examples, see [Customizing MathJax](../editing/math-and-diagrams.md#customizing-mathjax).

## VNote crashes after a version update

This often happens when the update spans several versions and an old configuration is no longer compatible. Open your **user** configuration folder and delete `vnotex.json`, then restart VNote. See [Settings](../customization/settings.md) for where that folder is.

## The interface freezes, the cursor is invisible in edit mode, or VNote crashes when opening a note

On **Windows**, these three symptoms are usually caused by the display-card driver. Work through these steps, restarting VNote after each to check whether it helped:

1. Update your display-card driver.
2. Schedule VNote to run with the integrated display card.
3. If that doesn't help, try each `OpenGL` value one by one in **Settings**.
4. Make sure VNote's executable folder is on the `C:` drive.

## Where are my notes stored?

Wherever you put them. Each notebook has a directory called its *Notebook Root Folder*. Ordinary Markdown notes remain plain files, and separate images are stored in an assets folder (`vx_assets` by default); VNote's index and caches are separate from the content. Optional [encrypted notes](../managing-notes/encrypted-notes.md) in bundled notebooks are the exception: their bodies are not plaintext files for external editors. See [Notebooks, Folders & Notes](../managing-notes/notebooks-folders-notes.md).

## How do I sync my notes across devices?

Bundled notebooks support built-in **Git**, **WebDAV** (including Nextcloud), and **Jianguoyun (WebDAV)** sync. External folder-sync tools such as Dropbox or OneDrive remain an alternative; do not let competing sync methods modify the same notebook at the same time. See [Notebook Sync](../managing-notes/notebook-sync.md).

## Can I use VNote portably (from a USB drive)?

Yes. Bundle the configuration next to the executable as described in [Make VNote portable](../customization/settings.md#make-vnote-portable).

## How do I import my existing Markdown files?

Create a **bundled notebook** and import your folder into it — see [Importing & Migrating](../managing-notes/importing-migrating.md). If you would rather adopt the existing folder exactly as it is, open it with **New Notebook → Type: Raw notebook**, which browses it in place but has no tags, attachments, or recycle bin. For migrating from other apps, see [Data Migration](data-migration.md).

## Why did my note open in a separate window?

That window is a **detached view**. A [Quick Note](../productivity/quick-note.md) scheme can be configured to open notes there. It appears when you use **Detach** on a tab, **Open as Detached** in the notebook explorer, or the `--detached-view` [command line](../getting-started/command-line.md) option. Close it or drag its tab back to return the note to the main window — see [Editor Basics](../editing/editor-basics.md#detached-windows).

## Does VNote update itself?

Not without your action. Ordinary checks remain check-only; on Windows, the startup update notification also offers **Update Now** to launch an external updater after you explicitly choose it. Other platforms use manual updates. See [Checking for updates](../getting-started/installation.md#checking-for-updates).

## What is the difference between a bundled and a raw notebook?

A bundled notebook keeps an index under its root folder, and that index is what enables tags, attachments, the recycle bin, built-in Git/WebDAV/Jianguoyun sync, and optional note-body encryption. A raw notebook has no index — it browses a folder in place, like a file browser — so those features are unavailable. Prefer bundled, and choose raw only when the existing folder must be adopted as it is, or is managed outside VNote. See [Notebooks, Folders & Notes](../managing-notes/notebooks-folders-notes.md#which-type-should-i-use).

# FAQ

Answers to common questions and fixes for issues people hit most often. If your question isn't here, check the rest of the docs or the project's [GitHub issues](https://github.com/vnotex/vnote/issues).

## How do I specify a custom MathJax script? { #custom-mathjax }

VNote uses **MathJax 3** to render math. To choose which MathJax build it loads:

1. Copy `web/js/mathjax.js` from the **default** configuration folder into the same path (`web/js/mathjax.js`) under your **user** configuration folder. VNote will use your copy instead of the default.
2. Edit the copied file and set the script URL. The default is:

    ```js
    this.mathJaxScript = 'https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-svg.js';
    ```

To use a **local** copy for offline use, [download MathJax](https://docs.mathjax.org/en/latest/web/hosting.html) and point to it:

```js
this.mathJaxScript = 'file://c:/Users/foo/mathjax/tex-svg.js';
```

See [Math & Diagrams](../editing/math-and-diagrams.md) and [Settings](../customization/settings.md) for context.

## VNote crashes after a version update

This often happens when the update spans several versions and an old configuration is no longer compatible. Open your **user** configuration folder and delete `vnotex.json`, then restart VNote. See [Settings](../customization/settings.md) for where that folder is.

## The interface freezes, the cursor is invisible in edit mode, or VNote crashes when opening a note

On **Windows**, these three symptoms are usually caused by the display-card driver. Work through these steps, restarting VNote after each to check whether it helped:

1. Update your display-card driver.
2. Schedule VNote to run with the integrated display card.
3. If that doesn't help, try each `OpenGL` value one by one in the **Settings** dialog.
4. Make sure VNote's executable folder is on the `C:` drive.

## Where are my notes stored?

Wherever you put them. Each notebook is an ordinary directory (its *Notebook Root Folder*) containing plain Markdown files, with images kept in an assets folder (`vx_assets` by default). Nothing is hidden in a database. See [Notebooks, Folders & Notes](../managing-notes/notebooks-folders-notes.md).

## How do I sync my notes across devices?

VNote has a built-in Git sync for bundled notebooks, and — since a notebook is just a folder — you can also sync it with any tool you trust, such as Dropbox, OneDrive, or Nextcloud. See [Notebook Sync](../managing-notes/notebook-sync.md).

## Can I use VNote portably (from a USB drive)?

Yes. Bundle the configuration next to the executable as described in [Make VNote portable](../customization/settings.md#make-vnote-portable).

## How do I import my existing Markdown files?

Use **New Notebook** with **Type → Raw notebook** to build a notebook around an existing directory, or import files and folders into a notebook. See [Importing & Migrating](../managing-notes/importing-migrating.md). For migrating from other apps, see [Data Migration](data-migration.md).

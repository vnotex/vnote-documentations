# Data Migration

Because VNote works with plain Markdown files and images, moving your content into VNote is usually a matter of getting it into Markdown form and then building a notebook around it. VNote does not ship built-in importers for other note apps — development resources are limited — so this page collects third-party tools that help with common migrations.

!!! tip "Contribute a tool"
    If you have built a utility that helps migrate into VNote, get in touch so it can be listed here.

## First: build a notebook from your files

Whatever tool you export from, the goal is a folder of Markdown files. Once you have that, create a **bundled notebook** and import the folder into it — see [Importing & Migrating](../managing-notes/importing-migrating.md). If you would rather adopt the folder exactly as it is, use **New Notebook** with **Type → Raw notebook** instead, keeping in mind that raw notebooks have no tags, attachments, or recycle bin.

## Migrating from common tools

- **Typora, Obsidian, and other Markdown editors** — these already store plain Markdown, so create a bundled notebook and import the folder. Use a raw notebook instead if you want to keep browsing that folder in place while another tool still manages its structure.
- **Apps without Markdown export** — export or convert to Markdown first (many tools can, or [Pandoc](https://pandoc.org/) can convert common formats), then build a notebook from the result.

## Migrating a VNote notebook itself

Moving a notebook between your own computers is different from importing from another app — it is just copying a folder and opening it. See [Notebook Sync](../managing-notes/notebook-sync.md).

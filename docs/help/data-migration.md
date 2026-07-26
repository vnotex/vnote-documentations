# Data Migration

Because VNote works with plain Markdown files and images, moving your content into VNote is usually a matter of getting it into Markdown form and then building a notebook around it. VNote does not ship built-in importers for other note apps — development resources are limited — so this page collects third-party tools that help with common migrations.

!!! tip "Contribute a tool"
    If you have built a utility that helps migrate into VNote, get in touch so it can be listed here.

## First: build a notebook from your files

Whatever tool you export from, the goal is a folder of Markdown files. Once you have that, use **New Notebook** with **Type → Raw notebook** to turn it into a notebook without moving anything — see [Importing & Migrating](../managing-notes/importing-migrating.md).

## Migrating from common tools

- **Typora, Obsidian, and other Markdown editors** — these already store plain Markdown, so point VNote at the folder with **New Notebook → Type: Raw notebook**.
- **Apps without Markdown export** — export or convert to Markdown first (many tools can, or [Pandoc](https://pandoc.org/) can convert common formats), then build a notebook from the result.

## Migrating a VNote notebook itself

Moving a notebook between your own computers is different from importing from another app — it is just copying a folder and opening it. See [Notebook Sync](../managing-notes/notebook-sync.md).

# Templates

A **template** is a starting point for a new note. Instead of facing a blank file every time, you can create a note that already contains your usual structure — a heading, front matter, standard sections — filled in automatically.

## Using a template

When you create a note, the **New Note** dialog lets you choose a template. The new note is created with that template's content instead of an empty body.

The dialog resolves the selection for you: it reuses the template you last picked for that file type in this session, otherwise the default configured for the file type, otherwise **None**. As soon as you choose a template by hand, VNote stops switching the selection under you.

Default templates per file type live under `newNoteDefaultTemplates` in `vnotex.json`, a plain map of file type to template name, seeded as `{"Markdown": "title.md"}`. See [Settings](../customization/settings.md) for where that file is.

## Built-in templates

VNote ships a `title.md` template — a first-level heading built from the note name, with the cursor waiting under it:

```md
# %no%

@@
```

!!! warning "Built-in templates are overwritten"
    The templates VNote ships are rewritten on every version bump. If you want to adapt one, **save it under a different name** — otherwise your changes disappear at the next update.

## Where templates live

VNote stores template files in the `templates` folder inside its configuration. **One file is one template.** You can add or delete templates directly in that folder using your system's file browser — no special import step is required. See [Settings](../customization/settings.md) for where the configuration folders are.

## Snippets in templates

Templates support [Snippets](snippets.md), which is what makes them dynamic. A template can call a snippet to fill in content automatically when the note is created.

For example, this template uses the built-in `%no%` snippet, which evaluates to the note name (without its suffix):

```md
# %no%
This is a template using a snippet to insert the note name as the title automatically.
```

If you create a note named `week report.md`, the new note becomes:

```md
# week report
This is a template using a snippet to insert the note name as the title automatically.
```

Any snippet works here, so templates can insert the current date, scaffold code blocks, position the cursor, and more. Combine templates with snippets to make new notes that are ready to write in immediately.

Because `title.md` does this out of the box, the separate **Insert file name as title** option no longer exists — set a default template instead.

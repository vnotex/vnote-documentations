# Templates

A **template** is a starting point for a new note. Instead of facing a blank file every time, you can create a note that already contains your usual structure — a heading, front matter, standard sections — filled in automatically.

## Using a template

When you create a note, the **New Note** dialog lets you choose a template. The new note is created with that template's content instead of an empty body.

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

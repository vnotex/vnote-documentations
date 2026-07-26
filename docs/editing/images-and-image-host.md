# Images & Image Host

Notes often need pictures, and VNote makes images painless: paste one and it is saved into your notebook and linked automatically. When you want to share a plain Markdown file without shipping the image files, an **image host** stores your pictures online instead.

## Inserting images

The fastest way to add an image is to **paste** it (a screenshot, or an image copied from elsewhere) directly into the editor. VNote:

1. Saves the image file into the notebook — by default in a `vx_images` folder next to the note.
2. Inserts the Markdown link for you.

You can also insert an image from a file, or drag and drop one into the editor. Because images live inside the notebook, they travel with it when you copy or [sync](../managing-notes/notebook-sync.md) the notebook.

```md
![alt text](vx_images/example.png)
```

## Local images vs. image host

VNote supports two storage strategies, and you can switch between them per note in the editor:

- **Local images** — files are stored inside the notebook. Self-contained and offline-friendly.
- **Image host** — images are uploaded to an online service, and the note links to the online URL. The Markdown file then references nothing local, so you can share the plain text and readers see the images from anywhere.

A useful workflow when your connection is poor: insert images **locally** while writing, then **upload all images** in the note to an image host at the end.

## What an image host is

An **image host** is an online service that holds your images. Unlike local images, an image-hosted note carries no image files with it — you can hand someone just the Markdown text and they still see every picture, loaded online.

## Setting up an image host

First configure an image host in the **Settings** dialog. Then choose local images or the image host in the editor.

### GitHub / Gitee

Gitee follows a similar process; GitHub is used here as the example.

1. In GitHub, go to **Settings → Developer settings** and generate a new **Personal access token**.
2. Select the **repo** scope, generate the token, and copy it.
3. Create a **public** repository to hold the images. Generate the default `README` so the repository has an initial commit.
4. In VNote, add a new image host and fill in the **Personal Access Token**, **User Name**, and **Repository Name**.

Once configured, uploading an image (or all images in a note) pushes the files to that repository and rewrites the links to their online URLs.

## Tips

- Keep tokens private — treat a personal access token like a password.
- For portable, offline notes, prefer local images; for public sharing, prefer an image host.
- To tidy images gathered from many folders into `vx_images`, see the community tool noted in [Data Migration](../help/data-migration.md).

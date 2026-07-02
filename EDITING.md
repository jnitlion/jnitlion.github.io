# How to Edit Your Website — Step-by-Step Guide

The site is plain HTML/CSS — no build tools, no frameworks. Every change
follows the same three-step rhythm:

> **1. Edit the file → 2. Preview locally → 3. Publish with git push**

Publishing takes about a minute: GitHub Pages redeploys automatically on
every push. And for any of this, you can simply ask Claude Code instead —
these instructions are the manual route.

---

## Previewing locally

Double-click `index.html` (or any page) — it opens in your browser. Refresh
the browser after saving edits. That's it; no server needed.

## Publishing your changes

Open PowerShell in the website folder (right-click → "Open in Terminal"):

```powershell
git add -A
git commit -m "Describe what you changed"
git push
```

Wait ~1 minute, then check https://jnitlion.github.io (hard-refresh with
Ctrl+F5 if you see the old version).

---

## Common tasks

### Edit text anywhere
Open `index.html` (or the page in `research/`, `news/`, `blog/`) in any text
editor — Notepad works. Find the text, change it, save, preview, publish.

### Add a news item
1. Copy any file in `news/` (e.g. `3mt-first-place.html`) to a new name,
   e.g. `news/defended-phd.html`.
2. Edit its `<title>`, the `<h1>`, the date, the summary text, and the
   photo slot.
3. In `index.html`, find `<ul class="news-list">` and copy the first
   `<li>...</li>` block to the TOP of the list (newest first). Update its
   `href`, date, and text.

### Add a blog post
1. Copy `blog/post-template.html` to e.g. `blog/my-topic.html`.
2. Write the post (the template shows headings, figures, code, quotes).
3. In `index.html`, find the `#blog` section and duplicate the post card;
   point it at the new file. Newest posts first.

### Add a photo or figure
1. Put the image file in `assets/` (use lowercase names, no spaces,
   e.g. `defense-photo.jpg`).
2. Find the dashed placeholder (`<div class="figure-placeholder" ...>`)
   where the image should go, and replace that whole div with:
   ```html
   <img src="../assets/defense-photo.jpg" alt="Describe the image">
   ```
   (Use `assets/...` without `../` if you're editing `index.html`.)
3. Update the `<figcaption>` below it.

### Add your headshot
In `index.html`, replace the `<div class="photo-placeholder" ...>...</div>`
block with:
```html
<img src="assets/headshot.jpg" alt="Portrait of Jester N. Itliong">
```

### Update the CV
1. Put the new PDF in `assets/` (e.g. `assets/Itliong_CV_Aug_2026.pdf`).
2. In `index.html`, search for `Itliong_CV_May_2026.pdf` (2 places) and
   update the filename.
3. Optionally delete the old PDF from `assets/`.

### Add a project card
In `index.html`, find the `#projects` section and duplicate an existing
`<a class="card card-link" ...>` block. Point it at a new page in
`projects/` (copy `stockmayer-simulator.html` as a starting skeleton) or
an external URL.

### Change colors or fonts
Everything is defined as CSS variables at the top of `css/style.css`
(`--ink`, `--accent`, `--bg`, fonts, etc.). Change once, applies everywhere.

### Add a new section to the main page
1. Copy an entire `<section id="..." class="section">...</section>` block
   in `index.html` and edit it.
2. Add a matching `<li><a href="#your-id">Name</a></li>` to the nav at the
   top of `index.html` AND to the nav in every page in `research/`, `news/`,
   `blog/`, and `projects/` (use `../index.html#your-id` there).
3. Keep backgrounds alternating by adding/removing `section-alt`.

---

## Things to know

- **Never publish drafts by accident:** root-level `.pdf`/`.docx` files are
  ignored by git on purpose (see `.gitignore`) — only `assets/` PDFs are
  published. Keep unpublished manuscripts out of `assets/`.
- **The ILThermo dashboard** lives in a separate repo
  (`Desktop/il-property-explorer` → github.com/jnitlion/il-property-explorer).
  Push there to update the app; Streamlit Cloud redeploys automatically.
- **If something looks broken after publishing**, the previous version is
  always recoverable: `git log --oneline` shows history, and
  `git revert <commit>` undoes a bad change safely.

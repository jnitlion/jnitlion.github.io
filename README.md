# Jester Itliong's Personal Academic Website

A single-page, static personal website for Jester (Jes) N. Itliong, Physics PhD
candidate at Michigan Technological University. Plain HTML/CSS with a small
amount of vanilla JavaScript. No frameworks, no build step.

## Structure

```
├── index.html      # main page (About, Research, Publications, Teaching, CV, News, Blog, Contact)
├── research/       # one article page per research project (linked from the Research cards)
├── projects/       # interactive projects (Stockmayer fluid simulator)
├── news/           # one page per news item (linked from the News list)
├── blog/           # blog posts; post-template.html is the starter/template post
├── css/style.css   # all styling, mobile-first responsive
├── js/main.js      # mobile nav toggle + active-section highlighting
└── assets/         # CV PDF (add headshot + figures here, e.g. headshot.jpg)
```

## Preview locally

Just open `index.html` in any browser — double-click it, or:

```powershell
start index.html        # Windows
open index.html         # macOS
```

Or serve it (avoids any file:// quirks):

```bash
python -m http.server 8000
# then visit http://localhost:8000
```

## Deploy to GitHub Pages (free)

1. Create a new repository on GitHub. For a `https://<username>.github.io` root
   site, name the repo `<username>.github.io` (e.g. `jnitlion.github.io`);
   any other name serves at `https://<username>.github.io/<repo-name>/`.

2. Push this folder to it:

   ```bash
   git init
   git add index.html research projects news blog css js assets README.md
   git commit -m "Personal website"
   git branch -M main
   git remote add origin https://github.com/jnitlion/jnitlion.github.io.git
   git push -u origin main
   ```

3. On GitHub: **Settings → Pages → Build and deployment**, set Source to
   **Deploy from a branch**, choose `main` and `/ (root)`, and save.

4. The site appears at `https://jnitlion.github.io` within a minute or two.
   Any future `git push` to `main` redeploys automatically.

## Customizing

- **Headshot:** drop a photo into `assets/` and replace the
  `.photo-placeholder` div in `index.html` with
  `<img src="assets/headshot.jpg" alt="Portrait of Jester N. Itliong">`.
- **Colors/fonts:** everything is defined as CSS variables at the top of
  `css/style.css`.
- **CV:** replace `assets/Itliong_CV_May_2026.pdf` with a newer file and update
  the two download links in `index.html` if the filename changes.
- **Research figures:** each page in `research/` has dashed "figure slot"
  placeholders. Put your image in `assets/` and replace the placeholder div
  with `<img src="../assets/your-figure.png" alt="...">`, then edit the
  `<figcaption>`.
- **New news item:** copy any page in `news/` to a new file, edit the title,
  date, photo slot, and summary, then add a matching `news-link` entry at the
  top of the `#news` list in `index.html` (newest first).
- **New blog post:** copy `blog/post-template.html` to a new file (e.g.
  `blog/my-topic.html`), write the post, then duplicate a card in the
  `#blog` section of `index.html` and point it at the new file. Keep newest
  posts first.

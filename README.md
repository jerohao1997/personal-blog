# Personal Blog — GitHub Pages

A minimalist technical blog. Drop a `.md` file in `posts/` and the blog updates automatically.

---

## Quick start

### 1. Create your GitHub Pages repo

```
yourusername/yourusername.github.io
```

Enable GitHub Pages from **Settings → Pages → Source: Deploy from branch (main, / root)**.

### 2. Configure `index.html`

Open `index.html` and edit the `CONFIG` block at the top of the `<script>` tag:

```js
const CONFIG = {
  siteName: "your.name",          // shown in header & footer
  tagline: "Notes on building things.",
  githubUser: "yourusername",     // your GitHub username
  githubRepo: "yourusername.github.io", // your repo name
  branch: "main",
};
```

Also update the **About** section and footer links in the HTML.

### 3. Push to GitHub

```bash
git init
git remote add origin git@github.com:yourusername/yourusername.github.io.git
git add .
git commit -m "initial"
git push -u origin main
```

Your blog is live at `https://yourusername.github.io`.

---

## Writing a post

Create a `.md` file in `posts/` using this naming convention:

```
posts/YYYY-MM-DD-your-post-slug.md
```

Every post needs front matter at the top:

```markdown
---
title: "Your Post Title"
date: 2024-04-01
description: "A one-sentence summary shown in the post list."
tags: [engineering, writing]
---

Your content starts here...
```

### Auto-update (recommended)

The included GitHub Action (`.github/workflows/update-index.yml`) watches for new `.md` files in `posts/` and automatically regenerates `posts/index.json`.

**How it works:**

1. You push a new `.md` file to `posts/`
2. The Action runs, updates `posts/index.json`, and commits it back
3. GitHub Pages redeploys — your post is live

No build step. No Jekyll. No Node.js required.

### Manual update (fallback)

If you prefer not to use the GitHub Action, edit `posts/index.json` yourself when you add a post:

```json
{
  "posts": [
    "2024-04-01-new-post.md",
    "2024-03-20-the-80-percent-problem.md",
    "2024-02-03-writing-documentation.md",
    "2024-01-15-hello-world.md"
  ]
}
```

Filenames are sorted newest-first (the blog renders them in this order).

---

## How posts are discovered

The blog tries three methods in order:

1. **GitHub Contents API** — `api.github.com/repos/{user}/{repo}/contents/posts` — works automatically on GitHub Pages, no config needed once `CONFIG` is set
2. **`posts/index.json`** — static file fallback, updated by the GitHub Action
3. **Hardcoded fallback** — the array in `fetchPostsList()` in `index.html`, for local development

---

## File structure

```
├── index.html              ← entire site (one file)
├── feed.xml                ← RSS stub
├── posts/
│   ├── index.json          ← post manifest (auto-updated)
│   ├── YYYY-MM-DD-slug.md  ← your posts
│   └── ...
└── .github/
    └── workflows/
        └── update-index.yml ← auto-updates index.json on push
```

---

## Customisation

All visual configuration is in `index.html`. The CSS uses variables:

```css
:root {
  --ink: #1a1a18;        /* main text */
  --accent: #c0392b;     /* red accent */
  --paper: #faf9f6;      /* background */
  --serif: 'Lora', ...;  /* body font */
  --mono: 'JetBrains Mono', ...; /* code/meta font */
}
```

Change `--accent` and fonts to make it yours.

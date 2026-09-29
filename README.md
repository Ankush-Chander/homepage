# homepage

Source for [ankushchander.com](https://ankushchander.com): a personal homepage, blog and
recommendations list built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

## Layout

| Path | What it holds |
| --- | --- |
| `docs/index.md` | Home page |
| `docs/blog/posts/` | Blog posts, one Markdown file each |
| `docs/recommendations.md` | Recommendations page |
| `docs/images/` | Profile photo and social icons |
| `docs/CNAME` | Custom domain, copied into the built site |
| `hooks/socialmedia.py` | Appends "Share on X / Facebook" buttons to blog posts |
| `mkdocs.yml` | Navigation, theme, plugins (blog, RSS) and social links |

## Run locally

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve            # http://127.0.0.1:8000, reloads on save
```

## Write a blog post

Add a file under `docs/blog/posts/`. The filename becomes the URL slug
(`find_heart.md` → `/blog/find-heart/`).

```markdown
---
draft: false
date: 2026-09-05
categories:
  - career
description: "One-line summary, used in the post listing and RSS feed."
---

Body…
```

- The title comes from the first `#` heading, or from the filename when there is none.
- `draft: true` keeps the post out of the published site.
- `date` drives ordering, the archive and the RSS creation date.
- `categories` build the category pages and RSS categories.

## Feeds

The RSS plugin publishes feeds for everything under `blog/posts/`:

- `/rss.xml` and `/feed.json` — ordered by creation date
- `/rss-updated.xml` and `/feed-updated.json` — ordered by last update

## Deploy

GitHub Pages serves the `gh-pages` branch. Build and push it with:

```bash
mkdocs gh-deploy
```

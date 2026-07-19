# teo's codex

A hand-built Jekyll theme — minimal and centered: one narrow column for header,
body, and footer, set entirely in a single serif, with a single rubric-red accent and
a candle you light to enter the dark. Dual light/dark with a smooth cross-fade. No purchased theme.

## Deploy (GitHub Pages — zero config)

1. Put these files in a repo (e.g. `teocos/teocos.github.io`, or any repo).
2. Push to the `main` branch.
3. **Settings → Pages →** *Deploy from a branch* → `main` / `/ (root)`.
4. **Custom domain:** the `CNAME` file already contains `teocos.com`. In your DNS,
   point an `ALIAS`/`ANAME` (or four `A` records) at GitHub Pages and a `CNAME`
   for `www` → `teocos.github.io`. GitHub's docs list the current IPs.
5. Tick **Enforce HTTPS** once the cert is issued.

GitHub builds the site with the same `github-pages` gem pinned in the `Gemfile`,
so what you preview locally is what ships.

## Preview locally

```sh
bundle install
bundle exec jekyll serve      # http://localhost:4000
```

(Analytics only loads in production, so local previews stay clean.)

## Before you ship

- **Favicon:** drop your `favicon.ico` into `assets/` (the theme links `/assets/favicon.ico`).
- **GitHub username:** set `social.github` in `_config.yml` if it isn't `teocos`.
- **Ko-fi / Analytics:** already wired (`kofi: teocos`, `google_analytics: G-LR2601DRCQ`).

## Write a new entry

Create `_posts/YYYY-MM-DD-a-slug.md`:

```yaml
---
title: "Your Title Here"
date: 2026-07-20
tags: [engineering, robotics]         # first tag shows in the record line
ref: "optional-reference-code"        # optional; shows as "Ref …"
image: /assets/img/cover.jpg          # optional cover (local is best)
image_alt: "Describe the image"
image_caption: "Plate 002 — a caption"
description: "One line for search + social previews."
---

Your opening paragraph — this gets the rubricated drop-cap, so start on text.

## First Section

Sections written as `##` are auto-numbered with rubric § marks.
A table of contents appears automatically when a post has 3+ sections.
Reading time is calculated for you.
```

That's it — tags pages, the archive, RSS, sitemap, prev/next, and the TOC all
update themselves.

## What's where

- `_config.yml` — identity, links, topics, pagination.
- `assets/css/style.css` — the whole design system, plain CSS (edit tokens at the top to retune).
- `_includes/head.html` — SEO/OG/JSON-LD. `_includes/header.html` — masthead + candle toggle.
- `_layouts/` — `post`, `page`, `default`.
- `assets/img/og-default.png` — the social-share card (regenerate anytime).

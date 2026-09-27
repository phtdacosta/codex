# teo's codex

A hand-built Jekyll theme for GitHub Pages. One quiet column in two inks, lamp-black and
vermilion, on bone paper. The woodcut candle in the top-right corner is the light/dark
switch, and dark mode is the reverse print, lit by it. Every post is a numbered decree (the
oldest is Nº 001). Plain CSS, no build step, no purchased theme.

## Deploy (GitHub Pages, zero config)

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

## Write a new entry

Create `_posts/YYYY-MM-DD-a-slug.md`:

```yaml
---
title: "Your Title Here"
date: 2026-10-20
tags: [engineering, robotics]         # the first tag shows in the docket line
ref: "optional-reference-code"        # optional; shows as "Ref …"
image: /assets/img/cover.jpg          # optional plate (local is best); printed in the two inks
image_alt: "Describe the image"
image_caption: "Plate 005 — a caption"
description: "One line for search + social previews."
# last_modified_at: 2026-11-02        # after a real revision: shows "Revised …" and updates search dates
---

Your opening paragraph. It gets the red drop cap, so start on text.

## First Section

Sections written as `##` get § marks (§ I, § II …).
A Contents box appears when a post has 3+ sections (`toc: false` hides it).
```

The Nº, reading time, tags page, RSS, sitemap, `llms.txt` and Newer/Older links all
update themselves.

## Annexes (companion documents)

A long piece can carry annexes (its references, a research program, an appendix) that
belong to it instead of standing as posts of their own. Put each one in
`_annexes/<the-post's-slug>/<name>.md`:

```yaml
---
layout: annex
title: "Your Title Here: References"  # full title (browser tab, search, social)
short_title: "References"             # the name shown on the page and in the lists
parent: a-slug                        # the post's file name without the date and .md
annex: A                              # its letter
date: 2026-10-20                      # use the post's date
description: "One line for search + social previews."
# toc_style: index                    # for many short sections (a glossary A–Z)
---
```

It's published at `/YYYY/MM/<the-post's-slug>/<name>/`. The post lists it in its Contents
and again after the text, the home page marks the post "+ 1 annex", and the annex opens
with "Nº … · Annex A" and a link back. Annexes stay out of the home list, the numbering,
RSS, the tags page and the Newer/Older links, and appear under their post in `llms.txt`,
`llms-full.txt` and the sitemap. When an existing post becomes an annex, add its old
address under `redirect_from:` (see the two Fate annexes): old links keep working, and
keep their `#anchor`.

The two files left in `_posts/` for the old Fate companions are empty stubs marked
`published: false`. They can be deleted.

## What's where

- `_config.yml` — identity, links, newsletter, the founding year in the strip (`founded`), the motto's gloss.
- `assets/css/style.css` — the whole design system, plain CSS (tokens at the top).
- `_includes/lamp.html` — the candle (theme switch). `header.html` — the top strip.
  `footer.html` — the motto line. `head.html` — SEO / Open Graph / JSON-LD.
  `toc.html` — the Contents box. `decree-no.html` — the Nº numbers.
  `annexes.html` — a post's annexes after its text. `newsletter.html` — the Google Forms box.
- `_layouts/` — `default`, `post`, `annex`, `page`, `redirect` (old addresses), `none` (plain text files).
- `assets/favicon.ico` — the tab icon. `assets/img/og-default.png` — the default social-share card.

`theme: null` in `_config.yml` keeps GitHub's default theme (Primer) out of the build;
its own stylesheet would otherwise be built to the same address as this one.

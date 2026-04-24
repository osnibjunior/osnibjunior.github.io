# osnibjunior.dev

Personal blog of **Osni B. Junior** — technical and non-technical writing. Built with [Jekyll](https://jekyllrb.com/) and hosted on GitHub Pages at [osnibjunior.dev](https://osnibjunior.dev).

## Run locally

Requires Ruby (>= 3.0) and Bundler.

```sh
bundle install
bundle exec jekyll serve
```

Then open <http://localhost:4000>.

## Writing a post

Add a Markdown file to `_posts/` named `YYYY-MM-DD-slug.md` with front matter:

```yaml
---
layout: post
title: "Your title"
date: 2026-04-22 10:00:00 +0000
tags: [thoughts]
---
```

Use `<!--more-->` to mark where the home-page excerpt ends.

## Structure

- `_config.yml` — site config
- `_layouts/` — page shells (`default`, `home`, `post`)
- `_includes/` — header, footer, theme toggle
- `_posts/` — blog posts in Markdown
- `assets/css/style.scss` — styles with dark/light theme variables
- `assets/js/theme.js` — theme toggle (persisted in `localStorage`)

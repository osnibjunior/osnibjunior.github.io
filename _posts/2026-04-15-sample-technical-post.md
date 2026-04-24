---
layout: post
title: "Notes on shipping small static sites in 2026"
date: 2026-04-15 09:00:00 +0000
tags: [tech, jekyll]
---

Static sites are having a quiet renaissance. Not the kind that trends on Hacker News every six months, but the kind where people who just want a personal site keep reaching for the same small set of tools — and it mostly Just Works.

<!--more-->

## Why Jekyll, still

GitHub Pages builds Jekyll natively. That's the whole pitch. No CI to configure, no Node toolchain to keep alive, no lockfile drama. You write Markdown, push to `main`, and a few seconds later the site is live.

There are faster builders (Hugo), prettier DX stories (Astro), and friendlier plugin ecosystems (11ty). All true. But for a personal blog — where the build runs once a week and nobody cares if it takes four seconds — the "zero moving parts" story is hard to beat.

## The pieces that matter

A personal blog really only needs:

1. A **layout system** so the header and footer don't live in every file.
2. A **post list** that reverses itself automatically.
3. A **tag system** — optional, but nice to have.
4. **Dark mode** — table stakes at this point.

Everything else is polish.

## A dark-mode detail worth knowing

The one trap with dark mode is the *flash of wrong theme* on first paint. The fix is a small inline script in the `<head>` that applies `data-theme` before the CSS loads:

```html
<script>
  var stored = localStorage.getItem('theme');
  var prefersDark = matchMedia('(prefers-color-scheme: dark)').matches;
  document.documentElement.setAttribute(
    'data-theme',
    stored || (prefersDark ? 'dark' : 'light')
  );
</script>
```

That's it. Render-blocking, yes, but it's 200 bytes and it saves you the eye-searing white flash every time someone with dark mode enabled lands on your site.

## Closing thought

Boring tools for boring problems, fancy tools for fancy problems. A personal blog is a boring problem — and that's a feature.

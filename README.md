# ChrisNeff.github.io

Personal blog at https://chrisneff.github.io/, built with [Astro](https://astro.build) on the [AstroPaper](https://github.com/satnaing/astro-paper) theme (v7.2.0, MIT, see `LICENSE`) in Pittsburgh black and gold. GitHub Actions builds and deploys it on every push to `main`.

## Write a post

Add a Markdown (`.md`) or MDX (`.mdx`) file to `src/content/posts/`. The file name becomes the URL (`my-post.md` → `/posts/my-post/`). Files or folders starting with `_` are ignored. Frontmatter:

```yaml
---
title: "Post title"
description: "One sentence for post lists, RSS and social previews."
pubDatetime: 2026-11-18T12:00:00-05:00
modDatetime: 2026-11-20T09:00:00-05:00 # optional, when you update a post
tags:
  - meta
featured: false # optional, pins the post to the top of the home page
draft: true # optional, keeps the post off the site
---
```

Push to `main` and the site rebuilds in a minute or two.

## Run locally

Requires Node 22.23.4 or newer and pnpm (`brew install pnpm`).

```sh
pnpm install
pnpm dev      # http://localhost:4321, live reload
pnpm build    # type check, production build into dist/, search index
pnpm preview  # serve dist/
```

## Where things live

- `astro-paper.config.ts`: site title, description, social links, share links, features
- `src/content/posts/`: posts
- `src/content/pages/about.md`: About page
- `src/styles/theme.css`: colors (light and dark)
- `.github/workflows/deploy.yml`: build and deploy

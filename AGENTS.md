# ChrisNeff.github.io

Chris Neff's personal blog: Astro on a vendored copy of the AstroPaper theme, deployed to https://chrisneff.github.io/ by GitHub Actions. README.md covers writing a post, frontmatter, and local commands.

## Changes go through a pull request

`main` is the live site: every merge to it deploys. A repository ruleset requires a pull request and a passing `check` job (`.github/workflows/ci.yml`) before anything lands on `main`, so a direct push is rejected.

1. Branch from an up-to-date `main` with a short descriptive name (`post-azure-landing-zones`, `fix-rss-dates`).
2. Run `pnpm build` locally. Done when it finishes with `0 errors` from `astro check` and Pagefind reports the expected page count.
3. Commit, push the branch, and open the PR with `gh pr create`. Body format: a 1-3 sentence plain opener saying what changes and why, then the full detail (changes, verification) inside `<details><summary>MODEL NAME</summary>`.
4. Chris reviews and merges. Leave the merge to him unless he says otherwise.

Commits: concise imperative subject, authored with Chris's personal email (check `git config user.email` before the first commit), no `Co-Authored-By` lines.

## Posts are Chris's voice

Every post publishes under Chris's name, so the words are his.

- Draft a post only when asked, and show the full text for approval before committing it.
- Use hyphens or commas for asides (no em-dashes) and American spelling.
- Keep work content generic: name no client, employer, colleague, or customer. "Consulting" and anonymized technical lessons are fine.
- Set `pubDatetime` with the `-05:00` / `-04:00` offset for the day it publishes. The site timezone is `America/New_York`.

## Theme customizations

AstroPaper v7.2.0 (MIT, copyright notice in `LICENSE`) was copied in, not installed as a package, so there is no upstream update path: a theme upgrade means diffing against a new AstroPaper release by hand and keeping these local changes:

- `astro-paper.config.ts`: site identity, socials (GitHub, X), share links, `editPost` off.
- `src/styles/theme.css`: Pittsburgh black and gold. Dark mode uses gold `#ffb612` on black `#101820`. Light mode uses the darker gold `#8a5a00`, because `#ffb612` on a light background is 1.6:1 contrast; keep every text color at WCAG AA (4.5:1) or better.
- `src/pages/index.astro`: hero shows the site title and description in place of the theme's intro text.
- Removed: the theme's sample posts and images, Docker files, its PR CI, Dependabot config, and GitHub community templates.

## Gotchas

- Pagefind search indexes post bodies only, so a word that appears only in `description` is not searchable.
- `pnpm` is pinned through `packageManager` in `package.json`, and pnpm 12 records that pin in `pnpm-lock.yaml`. Change the version in `package.json` and run `pnpm install` so both stay in step.
- Files and folders under `src/content/posts/` whose names start with `_` are excluded from the site.

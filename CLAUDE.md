# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

Personal academic website for Steve Geinitz, hosted on GitHub Pages at sgeinitz.github.io. Built with Jekyll using the `jekyll-theme-minimal` theme.

## Local Development

```bash
bundle exec jekyll serve
```

There is no build step beyond what GitHub Pages does automatically on push to `main`. No tests or linter are configured.

## Architecture

- **Jekyll theme**: `jekyll-theme-minimal` (configured in `_config.yml`), with a custom `_layouts/default.html` that overrides the theme's default layout
- **Single-page site**: `index.md` is the only content page; it uses anchor-based navigation (`#bio`, `#teaching`, `#projects`, `#publications`)
- **Left-hand nav**: `_includes/left-nav.html` renders section links; only shown on the home page (controlled by `{% if page.url == "/" %}` in `default.html`)
- **Navigation data**: `_data/navigation.yml` defines top-level nav items (Home, Presentations, CV, Blog, Workshops) — not all of these have corresponding pages yet
- **Custom CSS**: `assets/css/custom.css` — flexbox layout for sidebar + content, responsive breakpoint at 700px
- **Per-page CSS**: Supported via `page_css` front matter (loaded in `default.html`); site-wide custom CSS is set in `_config.yml` under `page_css`
- **Google Analytics**: Tag `G-1NMPN6CTJN` injected via `_includes/head-custom-google-analytics.html`
- **Static assets**: Profile images in `img/` (multiple sizes: 32, 48, 96, 128px), CV PDF in `cv/`

## Key Config (`_config.yml`)

Site-level variables (`site.logo`, `site.profile_gh`, etc.) are referenced in `default.html` to render the header profile image and social media icon links.

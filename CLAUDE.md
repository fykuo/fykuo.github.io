# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static single-page Buddhist dharma archive website for Guo Yu (果煜), hosted on GitHub Pages at `fykuo.github.io`. The entire site lives in a single file: `index.html`. There is no build system, no package manager, and no dependencies to install.

## Running Locally

Serve with any static HTTP server — no build step required:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Architecture

Everything is in `index.html`:

- **CSS variables** at the top of `<style>` define the color palette (earth tones / traditional Chinese aesthetic).
- **Card grid**: Each archive item is a `<div class="card">` with a `data-tags` attribute containing space-separated keywords used for search filtering.
- **Client-side search**: `filterContent()` reads the search input and hides/shows cards by matching against the card's inner text and `data-tags`. No network requests are made.
- **Navigation**: Cards link to subdirectories (e.g., `./2025孟子選註與講評/`) that are separate content folders not tracked in this repo root.

## Content Conventions

When adding a new archive card:
1. Copy an existing `<div class="card">` block.
2. Set `data-tags` to space-separated keywords in both Chinese and English for searchability.
3. The `href` on the card should point to the subdirectory that holds the actual content files.
4. Cards are ordered newest-first (descending by year).

## Styling Conventions

- All colors are defined as CSS variables (`--primary-color`, `--accent-color`, etc.) — do not use hard-coded hex values in new rules.
- Fonts are Noto Serif TC (body) and Noto Sans TC (UI/headers), loaded from Google Fonts.
- Mobile breakpoint is `600px`.

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running locally

```bash
docker-compose up
```

Serves the site at `http://localhost`. No build step — Caddy serves `site/` as a static file server.

## Architecture

This is a **single-file SPA**: all HTML, CSS, and JavaScript live in `site/index.html`. There is no build toolchain, no package manager, and no framework dependencies.

- `site/index.html` — the entire website (~43 KB, fully self-contained)
- `site/favicon.svg` — SVG favicon
- `Caddyfile` — Caddy config (HTTP file server on port 80)
- `docker-compose.yml` — runs Caddy with `site/` mounted as the document root

External resources loaded at runtime: Google Fonts (Fraunces, JetBrains Mono, Manrope).

## i18n system

Translations are stored as a JS object (`translations`) keyed by language code (`nl`, `en`). DOM elements carry `data-key` attributes; the `setLanguage(lang)` function swaps text content while preserving inline `<em>` tags. The selected language is persisted in `localStorage`. Text changes use a morphing animation.

## Design tokens

All visual values are CSS custom properties on `:root`. Key ones:

| Property | Value |
|---|---|
| `--bg` | `#0b0b0c` (near-black background) |
| `--accent` | `#ff9443` (amber) |
| `--text` | `#e8e3d9` |

Responsive breakpoints: 900 px, 820 px, 720 px, 680 px, 360 px.

## Known placeholders

`site/index.html` contains two unfilled values:
- `KVK · [NUMMER IN TE VULLEN]`
- `BTW · [NUMMER IN TE VULLEN]`

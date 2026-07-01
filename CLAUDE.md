# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a static personal portfolio website (elina.dev) for a mobile engineer. There is no build system, no package manager, and no dependencies — it is pure HTML/CSS/JS.

## Development

Open the site locally by opening `index.html` directly in a browser, or use any static file server:

```bash
python3 -m http.server 8080
```

There are no build, lint, or test commands.

## Architecture

The entire site lives in a single file: **`index.html`**.

- All CSS is inline in a `<style>` block in the `<head>`.
- All JavaScript is inline at the bottom of `<body>`.
- No external frameworks or libraries — only Google Fonts.

**CSS design tokens** are defined as CSS custom properties on `:root`:
- Colors: `--ink`, `--paper`, `--amber`, `--slate`, `--mint`, etc.
- Typography: `--font-display` (Space Grotesk), `--font-body` (Inter), `--font-mono` (JetBrains Mono)
- Spacing/radius: `--radius-card`, `--radius-btn`, `--radius-pill`
- Motion: `--ease-standard`, `--dur-fast`, `--dur-base`

**Page sections** (navigated via anchor links): `#top` (hero), `#about`, `#skills`, `#work`, `#writing`, `#teaching`, `#contact`.

**Assets** are in the `assets/` folder: project screenshots (PNG) and a profile photo (JPG).
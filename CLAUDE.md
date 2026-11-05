# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static portfolio site (elinahovakimyan.com) for **Eleene** — the AI creative studio of Elina Hovakimyan (AI product visuals, cinematic AI films, AI websites, AI mobile apps). No build system, no package manager, no dependencies — pure HTML/CSS/JS. The only call to action is Instagram: https://www.instagram.com/eleene.ai/ . No prices are shown anywhere. **Never mention Elina Hovakimyan by name on the site** (copy, meta, schema, alt text) — the brand is Eleene and copy focuses on service quality and possibilities. Tone: surreal, whimsical, luxurious.

## Development

```bash
python3 -m http.server 8080
```

There are no build, lint, or test commands.

## Architecture

The homepage lives in a single file: **`index.html`** (inline `<style>` in the head, inline `<script>` at the end of body, Google Fonts only).

- **Design tokens** on `:root`: colours `--paper`, `--ink`, `--rouge`, `--gold`, `--night`, `--moon`…; fonts `--font-display` (Cormorant Garamond) and `--font-body` (Jost); `--gutter`, `--ease`.
- **Sections** (museum "rooms"): `#hero` (tiles orbiting the headline), `#collection` (statement), `#rouge` (Room I, pinned horizontal walk), `#ivory` (Room II, editorial grid + falling petals), `#source` (Room III, product campaign), `#quiet` (Room IV, swipe cabinet), `#films` (screening room, dark, fireflies canvas), `#digital` (dreamy browser + phone showcase cycling our own imagery via `[data-cycle]`, four promise cards — keep it warm, never technical), `#services` (quality + "what becomes possible" per service), `#studio` ("The Eleene standard" — three principles, no personal bio), `#faq`, `#contact`. In the hero, every `[data-orbit]` element (six tiles + the spinning seal) slowly orbits the headline on an ellipse (`sizeOrbit` / `orbitStep`); each tile also cross-fades through its own images. The headline never fades on scroll.
- **Living layer (JS):** `.flower-slot[data-flower]` placeholders are replaced by SVG flowers that grow with scroll (`mx`/`my` = mobile position); `FLIGHTS` defines scroll-driven critters per section (`kind`: fly / swim / plane / float — butterflies, koi, paper plane, hot-air balloon); `[data-clouds]` JSON spawns drifting clouds; bubbles in Source, moon in Films, sparkle cursor trail on desktop; `[data-par]` = parallax speed; `.reveal` / `[data-fade]` = reveal on view; everything is disabled under `prefers-reduced-motion`.
- **Lightbox:** any element with `data-lb="<file key>"` opens `assets/work/<key>.webp`; `data-film="<key>"` opens `assets/films/<key>.mp4`.

## Assets

- Original full-resolution source files are kept outside the repo (removed from `assets/portfolio/` to keep deploys small).
- `assets/work/` — optimized WebP: `<key>.webp` (1600w) and `<key>-sm.webp` (760w) .
- `assets/films/` — `<key>.mp4` (720p with sound), `<key>-loop.mp4` (silent preview), `<key>-poster.jpg`.
- `assets/og-image.jpg` — 1200×630 social card. `assets/opt/` is still used by the archive pages.

To add a piece: export both WebP sizes into `assets/work/`, then copy a `<figure class="piece reveal" data-lb=…>` block. Keep `llms.txt` and `sitemap.xml` in sync for SEO/GEO.

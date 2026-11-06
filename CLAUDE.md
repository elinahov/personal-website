# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static portfolio site (elinahovakimyan.com) for **Eleene** — an independent, founder-led creative studio (product & campaign visuals, cinematic films & ads, websites & digital experiences, mobile apps). AI is an enabler, mentioned transparently but never the headline; surrealism is one visual language, not the positioning. No build system, no package manager, no dependencies — pure HTML/CSS/JS. Calls to action lead to the enquiry form in `#contact` (service CTAs carry `data-type` to preselect the project type) or to Instagram https://www.instagram.com/eleene.ai/ . No prices are shown anywhere. Use the founder's first name only ("Elina", in the founder section and schema) — never the full surname. First person singular for Elina's voice, "Eleene" for the brand; never imply a team. Voice: elegant, cinematic, editorial, curious, precise — avoid overusing dream / surreal / world / impossible / magic / luxury / flawless, and never fabricate clients, awards, guarantees or commissions. Label independent/spec work as such.

## Development

```bash
python3 -m http.server 8080
```

There are no build, lint, or test commands.

## Architecture

The homepage lives in **`index.html`**; **`websites-apps.html`** is a standalone digital portfolio page (same tokens and motifs, self-contained CSS/JS: hero with device frames, website exhibits Evoria (evoria.io/hy) + Aybora (aybora.app) as typographic browser covers linking to the live sites, then Eleene with real screenshots; five shipped apps as transparent cut-outs (no backgrounds), what's included, CTA to `index.html?type=website|app#contact`). Service and Digital CTAs on the homepage link to it ("Check my works"). The homepage itself is a single file (inline `<style>` in the head, inline `<script>` at the end of body, Google Fonts only).

- **Design tokens** on `:root`: colours `--paper`, `--ink`, `--rouge`, `--gold`, `--night`, `--moon`…; fonts `--font-display` (Cormorant Garamond) and `--font-body` (Jost); `--gutter`, `--ease`.
- **Nav:** Work · Films · Digital · Services · Studio · Contact. Directly under the hero, the running line (`.marquee`, a `<nav>`) is the service index: every word links to its service (`#svc-visuals`, `#svc-films`, `#svc-websites`, `#svc-apps`) and the line pauses on hover/focus.
- **Sections** (museum "rooms", each with `.room-line` headline, `.room-meta` commercial labels and a `.room-cta`): `#hero` (tiles orbiting the headline), `#collection` (statement), `#rouge` (Room I, pinned horizontal walk), `#ivory` (Room II, editorial grid + falling petals), `#source` (Room III, product campaign), `#quiet` (Room IV, swipe cabinet), `#halo` (Room V, product campaign: sticky arch stage that cross-fades between seven `.hstep` scenes while the section `--tone` shifts; tap opens the lightbox), `#films` (screening room, dark, fireflies canvas), `#digital` (dreamy browser + phone showcase cycling our own imagery via `[data-cycle]`, four promise cards — keep it warm, never technical), `#services` (four services: atmospheric intro + "What you can commission" list + CTA, then a combined-project invitation), `#studio` ("The person behind Eleene" — founder section; typographic "E" arch, never a photo of Elina), `#process` (four steps), `#standard` ("Imagined freely. Crafted beautifully." — three pillars), `#faq` (factual), `#contact` (enquiry form → mailto to `CONTACT_EMAIL`, or direct POST once `CONTACT_ENDPOINT` is set; see SETUP.md). In the hero, every `[data-orbit]` element (six tiles + the spinning seal) slowly orbits the headline on an ellipse (`sizeOrbit` / `orbitStep`); each tile also cross-fades through its own images. The headline never fades on scroll.
- **Living layer (JS):** `.flower-slot[data-flower]` placeholders are replaced by SVG flowers that grow with scroll (`mx`/`my` = mobile position); `FLIGHTS` defines scroll-driven critters per section (`kind`: fly / swim / plane / float — butterflies, koi, paper plane, hot-air balloon); `[data-clouds]` JSON spawns drifting clouds; bubbles in Source, moon + shooting stars in Films, sparkle cursor trail on desktop; **magic dust** (`stepDust`/`spawnMote`) spawns a few sparkles, glints, petals and dandelion seeds only while scrolling (one per ~140px, max 10 desktop / 6 mobile, mostly in the side margins, fading in 2.6–4.2s) — keep it subtle so reading is never disturbed; flights may set `mpts` for a mobile-specific path; `[data-par]` = parallax speed; `.reveal` / `[data-fade]` = reveal on view; everything is disabled under `prefers-reduced-motion`.
- **Lightbox:** any element with `data-lb="<file key>"` opens `assets/work/<key>.webp`; `data-film="<key>"` opens `assets/films/<key>.mp4`.

## Assets

- Original full-resolution source files are kept outside the repo (removed from `assets/portfolio/` to keep deploys small).
- `assets/work/` — optimized WebP: `<key>.webp` (1600w) and `<key>-sm.webp` (760w) .
- `assets/films/` — `<key>.mp4` (720p with sound), `<key>-loop.mp4` (silent preview), `<key>-poster.jpg`.
- `assets/og-image.jpg` — 1200×630 social card. `assets/opt/` is still used by the archive pages.

To add a piece: export both WebP sizes into `assets/work/`, then copy a `<figure class="piece reveal" data-lb=…>` block. Keep `llms.txt` and `sitemap.xml` in sync for SEO/GEO.

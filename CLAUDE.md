# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static landing page for the LudoTrace org. Single `index.html`, no build step, no framework. Deploys to `https://ludotrace.github.io/` via GitHub Pages from the root of this repo.

## Brand

Source assets live in the `brand/` repo (sibling to this one). Tokens:

| Token | Value | Use |
|-------|-------|-----|
| Background | `#12002e` | Page background |
| Cyan | `#00e5ff` | Signal line, labels, links |
| Magenta | `#ff2d78` | TRACE wordmark, event peaks, accent borders |
| Purple | `#c77dff` | Secondary markers, GitHub link |
| Font | `'Courier New', monospace` | Everything |

**Aesthetic rules** — carry these across any changes:
- No gradients. No border-radius on structural elements. No rounded organic shapes.
- Square stroke caps (`stroke-linecap: square`, `stroke-linejoin: miter`).
- Grid lines via CSS background-image at ~4% white opacity.
- All labels uppercase with wide letter-spacing (~0.4em).
- Terminal readout feel, not SaaS homepage.

## Heartbeat signal SVG

The hero signal is inline SVG with three strokes on the same polyline:
1. Dark glow shadow (`#1a0050`, thick)
2. Main cyan line (`#00e5ff`, 2.5px)
3. Faint highlight (`#a0f0ff`, 0.75px, 40% opacity)

Markers on the signal: magenta diamonds (`<polygon>`) on peaks, magenta squares (`<rect>`) on troughs, fading purple diamonds/squares along the baseline. Opacity decreases as markers move away from the active signal area. The avatar and banner SVGs in `brand/` are the reference for geometry.

## Page sections

Single scroll, in order: hero → one-liner → how it works (3 steps) → current mods → footer.

When adding a new game mod, add a card to the **current mods** section following the same pattern as the Fallout 4 card: left magenta border, game name, status, Nexus + GitHub buttons.

## Deployment

Push to `main` — GitHub Pages deploys automatically. `.nojekyll` in the repo root prevents Jekyll processing.

# AGENTS.md — LudoTrace Site

Canonical instructions for this repo. `CLAUDE.md` points here.

## What this is

The static landing page for the LudoTrace org. Single `index.html`, no build step, no
framework. Deploys to `https://ludotrace.github.io/` (and `ludotrace.com`) via GitHub Pages
from the root of this repo.

`STATUS.md` records what is actually live. Read it before starting work, update it after —
present-tense state, one line per item, no changelog. `git log -p --follow STATUS.md` is the
history.

## Brand

| Token | Value | Use |
|-------|-------|-----|
| Background | `#12002e` | Page background |
| Cyan | `#00e5ff` | Signal line, labels, links |
| Magenta | `#ff2d78` | TRACE wordmark, event peaks, accent borders |
| Purple | `#c77dff` | Secondary markers, GitHub link |
| Font | `'Courier New', monospace` | Everything |

**Aesthetic rules — carry these across any change:**

- No gradients. No border-radius on structural elements. No rounded organic shapes.
- Square stroke caps (`stroke-linecap: square`, `stroke-linejoin: miter`).
- Grid lines via CSS `background-image` at ~4% white opacity.
- All labels uppercase, wide letter-spacing (~0.4em).
- Terminal readout feel, not SaaS homepage.

The committed SVG and PNG assets in this repo are the geometry reference for anything new.

## Heartbeat signal SVG

The hero signal is inline SVG, three strokes on the same polyline:

1. Dark glow shadow (`#1a0050`, thick)
2. Main cyan line (`#00e5ff`, 2.5px)
3. Faint highlight (`#a0f0ff`, 0.75px, 40% opacity)

Markers: magenta diamonds (`<polygon>`) on peaks, magenta squares (`<rect>`) on troughs,
fading purple markers along the baseline, opacity decreasing with distance from the active
signal area.

## Page sections

Single scroll, in order: hero → one-liner → how it works (3 steps) → current mods → download
→ coming soon → community → footer.

When adding a game mod, add a card to **current mods** following the Fallout 4 card's
pattern: left magenta border, game name, status, Nexus + GitHub buttons.

## Client downloads

Binaries are hosted as GitHub Release assets on `ludotrace/client`, not in this repo. The
download buttons link straight to
`github.com/ludotrace/client/releases/latest/download/<asset>`, which always resolves to the
current release — no site push needed to update them.

This site still serves the update manifest the client checks on startup:

```
client/version.json   — update manifest, fetched by the client on startup
```

**Never edit `client/version.json` by hand, and never commit it from a local build.** The
client project's release pipeline writes it on every semver tag, pointing at that release's
GitHub asset URLs and checksums. A hand-placed file will be silently replaced, or worse,
served to users as a signed-for release it isn't.

## Deployment

Push to `main`; GitHub Pages deploys automatically. `.nojekyll` in the repo root prevents
Jekyll processing. The site is served at `ludotrace.com` through a Cloudflare-proxied CNAME,
with the custom domain also set in the repo's Pages settings.

**Pages is configured `build_type: legacy`, which requires that this repo have no
`.github/workflows` directory. Do not add one** — adding any workflow switches Pages to
Actions-based builds and breaks the deploy. Keep `STATUS.md` terse by hand rather than adding
a CI check for it. If a deploy fails, retry the build rather than changing `build_type`. See
`troubleshooting.md`.

## Scope

This repo is public and self-contained. Keep it that way:

- **Never reference a path, file, or issue number outside this repo.** No relative paths that
  climb out of the working tree, no pointers to private planning documents or infrastructure
  notes. If something here needs context that lives elsewhere, restate the part that matters
  in this repo's own words.
- **Never commit hostnames, tokens, or infrastructure detail** beyond the public
  `ludotrace.com` / `app.ludotrace.com` / `core.ludotrace.com` endpoints the page already
  links.

## Issues & PRs

GitHub, single remote (`github.com/ludotrace/ludotrace.github.io`). Issues and PRs both via
`gh` — pass `--repo ludotrace/ludotrace.github.io` when running outside a clone.

All changes go through a branch + PR, never directly to `main`. Branch naming:
`<type>/<short-description>`.

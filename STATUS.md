# Site Status

What is actually live on the LudoTrace landing page. Single `index.html`, no build step,
deployed via GitHub Pages.

Present-tense state only — no history, no rationale. `git log -p --follow STATUS.md` is the
changelog. There is deliberately no CI check for this file here: adding a workflow would
switch Pages off `build_type: legacy` and break the deploy.

---

## Verified end-to-end

- GitHub Pages deployment — a push to `main` goes live automatically; `.nojekyll` in place
- Landing page live with all sections: hero, one-liner, how it works, mods, download, coming
  soon, community, footer
- Custom domain `ludotrace.com` — `CNAME` committed, Cloudflare CNAME and Pages custom-domain
  config applied
- Fallout 4 mod card — Nexus Mods and GitHub links
- Stardew Valley mod card — Nexus Mods and GitHub links
- Brand assets committed: heartbeat avatar (PNG + SVG), favicon
- OG/Twitter meta tags wired
- Download buttons link to GitHub Release assets on `ludotrace/client` (`releases/latest/download/...`)
- Auto-update manifest — `client/version.json` served live, SHA-256 checksums matching the
  binaries attached to the corresponding GitHub Release
- "Join the waitlist" CTA — links to the app's waitlist screen, which is live and accepting
  signups (#10)

---

## Implemented, not yet validated

Nothing currently pending.

---

## Designed, not yet implemented

- Expanded launch/distribution surface beyond the current coming-soon callout
- Cloudflare hardening — bot fight mode, AI-crawler blocking, `security.txt`

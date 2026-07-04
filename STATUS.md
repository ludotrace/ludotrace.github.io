# Site Status

Static landing page for LudoTrace. Single `index.html`, no build step.
Deployed via GitHub Pages. Source: `ludotrace.github.io/`.

---

## Verified end-to-end

- GitHub Pages deployment — push to `main` goes live automatically; `.nojekyll` in place
- Landing page live at `https://ludotrace.github.io/` with all four sections: hero, one-liner, how it works, mods
- Fallout 4 mod card — Nexus Mods link (`nexusmods.com/fallout4/mods/106076`) and GitHub link present
- Stardew Valley mod card — Nexus Mods link (`nexusmods.com/stardewvalley/mods/48026`) and GitHub link present
- Brand assets committed: `avatar_heartbeat_v3.png`, `avatar_heartbeat_v3.svg`, `favicon.ico`
- OG/Twitter meta tags wired (image, title, description)
- Custom domain `ludotrace.com` — `CNAME` file present in repo, Cloudflare CNAME + GitHub Pages custom domain config applied; confirmed live 2026-07-03 (`https://ludotrace.com` returns 200 from GitHub Pages)
- Client binary hosting — all four binaries (`ludotrace.exe`, `ludotrace-mac-x64`, `ludotrace-mac-arm64`, `ludotrace-linux`) present in `downloads/`, written by the client release pipeline on `v0.1.0` (2026-06-29)
- Auto-update manifest — `client/version.json` live at `https://ludotrace.com/client/version.json`, confirmed 2026-07-03; SHA-256 checksums match the published binaries

---

## Implemented, not yet validated

- "Join the waitlist" CTA in the coming-soon callout, linking to `https://app.ludotrace.com/waitlist` (app repo `lt-app#11`, gitea PR #14). Not live until that app screen ships. Implements `ludotrace.github.io#10`.

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

---

## Implemented, not yet validated

- Nothing currently in this state for the site itself

---

## Designed, not yet implemented

- Custom domain `ludotrace.com` — no `CNAME` file in repo; Cloudflare CNAME and GitHub Pages custom domain config not yet applied (tracked in `internal/features.md` → Infrastructure)
- Client binary hosting — `downloads/` directory present and committed; binaries (`ludotrace.exe`, `ludotrace-mac-x64`, `ludotrace-mac-arm64`, `ludotrace-linux`) not yet deployed; written by client release pipeline on semver tag
- Auto-update manifest — `client/` directory present and committed; `client/version.json` not yet deployed; written by client release pipeline on semver tag

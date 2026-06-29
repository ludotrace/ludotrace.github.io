# ludotrace.github.io

Static landing page for [LudoTrace](https://ludotrace.github.io/) — game session insights, delivered without friction.

Single `index.html`, no build step, no framework. Deploys via GitHub Pages from the root of this repo.

## Structure

```
/               — landing page (index.html)
downloads/      — client binaries, written by the client release workflow
client/         — version.json manifest, written by the client release workflow
```

## Local development

Open `index.html` in a browser. No server required.

## Deployment

Push to `main` — GitHub Pages deploys automatically.

## Auto-update artifacts

The `ludotrace/client` release workflow pushes to this repo on every `v*` tag:
- `downloads/ludotrace-<os>-<arch>[.exe]` — built binaries
- `client/version.json` — version manifest consumed by the client updater

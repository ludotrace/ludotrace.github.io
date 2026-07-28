# ludotrace.github.io

Static landing page for [LudoTrace](https://ludotrace.github.io/) — game session insights, delivered without friction.

Single `index.html`, no build step, no framework. Deploys via GitHub Pages from the root of this repo.

## Structure

```
/               — landing page (index.html)
client/         — version.json manifest, written by the client release workflow
```

## Local development

Open `index.html` in a browser. No server required.

## Deployment

Push to `main` — GitHub Pages deploys automatically.

## Auto-update artifacts

Binaries are attached as GitHub Release assets on [`ludotrace/client`](https://github.com/ludotrace/client/releases) — this repo no longer hosts them. The download buttons link to
`github.com/ludotrace/client/releases/latest/download/<asset>`, which always resolves to the
current release.

The `ludotrace/client` release workflow still pushes `client/version.json` to this repo on
every `v*` tag — the version manifest consumed by the client updater, with platform URLs
pointing at that release's GitHub asset downloads.

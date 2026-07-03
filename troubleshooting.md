# Troubleshooting

## Pages deploy failed — do NOT flip `build_type` to `workflow`

Pages config is `build_type: legacy` and must stay that way. This repo has no
`.github/workflows`; it relies on GitHub's built-in Pages builder.

**Why a failed run is misleading:** the built-in builder runs as a *dynamically
generated* workflow named "pages build and deployment" (`event: dynamic`,
`path: dynamic/pages/pages-build-deployment`) with jobs `build → report-build-status →
deploy`, where the deploy step is literally "Deploy to GitHub Pages" (`actions/deploy-pages`).
So a failed run looks identical to an Actions-based deploy — same name, same `deploy-pages`
step — but its correct `build_type` is still `legacy`. The `deploy-pages` action in the logs
is NOT evidence of a user-defined workflow.

**"Deployment failed, try again later."** is GitHub's wording for a retryable, platform-side
flake. Fix is to retry, not reconfigure:

```
gh api -X POST repos/ludotrace/ludotrace.github.io/pages/builds   # rebuild current HEAD
gh api repos/ludotrace/ludotrace.github.io/pages/builds/latest    # watch status → "built"
gh api repos/ludotrace/ludotrace.github.io/pages --jq .build_type # must read "legacy"
```

Flipping `build_type` to `workflow` tells Pages to wait for a user workflow that doesn't
exist, turning a transient flake into a permanent failure and wedging in-flight builds.
(Happened once — 2026-07-03 — and cost a debugging session.)

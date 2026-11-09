# CLAUDE.md

## Project
- Root GitHub Pages site for the `gp-songtools` org: `https://gp-songtools.github.io/`
- Redirects and shared files only; every tool lives in its own repo at `/<repo>/`
- No build step, no dependencies; push to `main` deploys

## Directory map
- `index.html` — root → `/toolsmenu/`
- `suno-style-creator/index.html` — old GP Blueprint address → `/gp-blueprint/`
- `404.html` — forwards moved paths (`MOVED` map), else "not found" with a link to the menu
- `.nojekyll` — serve files as-is (needed for `.well-known/`)
- `README.md`, `CLAUDE.md`

## Rules
- A project repo's path always wins over a folder here; only add folders for names no repo uses
- When a tool's repo is renamed: add its old path to `MOVED` in `404.html` and an `<old>/index.html` redirect
- `404.html` also serves missing pages on tool sites without their own 404: keep it generic
- Redirect pages carry no analytics snippet (they redirect instantly; the target page counts the visit)
- Future: `.well-known/assetlinks.json` for the Android app (Trusted Web Activity) goes here
- Check layout at 390 px; colors via CSS vars with a `prefers-color-scheme: dark` override

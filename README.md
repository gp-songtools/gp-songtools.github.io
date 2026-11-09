# gp-songtools.github.io

The organisation's root GitHub Pages site. It holds no tool of its own; each tool is its own repo served at `gp-songtools.github.io/<repo>/`.

- `index.html` sends `gp-songtools.github.io/` to the [tools menu](https://gp-songtools.github.io/toolsmenu/).
- `suno-style-creator/` and `404.html` forward the old GP Blueprint address (`/suno-style-creator/…`) to `/gp-blueprint/…`.
- `404.html` is also the "not found" page for the tool sites that have none of their own.
- `.nojekyll` makes GitHub serve files as-is, so a future `.well-known/assetlinks.json` (Android app verification) is published.

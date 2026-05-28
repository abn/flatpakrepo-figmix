# flatpakrepo-figmix

Flatpak repository for [Figmix](https://gitlab.com/Valo27/figmix) — unofficial Figma desktop client for Linux — built and published via [aetherpak/actions](https://github.com/aetherpak/actions).

## Layout

- `apps/com.odnoyko.figmix/` — upstream source as a git submodule pointing at `https://gitlab.com/Valo27/figmix.git`.
- `.github/workflows/publish.yml` — single-app consumer of `aetherpak/actions/.github/workflows/publish.yml@v2`.

## Manifest

The Flatpak manifest lives in the upstream submodule at `apps/com.odnoyko.figmix/com.odnoyko.figmix.json`. Source paths inside the manifest (`generated-sources.json`, `"path": "."`) resolve relative to the manifest file, so no rewriting is needed.

## Updating the upstream

```
git submodule update --remote apps/com.odnoyko.figmix
git commit -am "Bump figmix submodule"
git push
```

The workflow on `main` triggers a rebuild and publishes to GitHub Pages + GHCR.

## Install

Once the first successful publish lands, the flatpakref will be available at the repo's Pages URL. Typical install:

```
flatpak install <pages-url>/com.odnoyko.figmix.flatpakref
```

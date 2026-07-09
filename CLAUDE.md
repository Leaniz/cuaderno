# Cuaderno — Coffee Brew Logger PWA

## What This Is

A self-contained PWA for logging coffee brews on a phone. Guided pour timer, 8-axis blind tasting radar, recipe library, Gist-based cloud sync. Built as a single HTML file with inline CSS/JS — no build step, no framework, no dependencies.

## Architecture

Everything lives in `index.html`. No bundler, no node_modules, no build.

- **State**: `localStorage` key `cuaderno-v1` holds all data (beans, equipment, brews). Sync credentials are in a separate `cuaderno-sync` key (never exported).
- **Service worker** (`sw.js`): cache-first for offline support. Bump the `CACHE` version string in `sw.js` whenever `index.html` changes — this triggers the update banner in the app.
- **Manifest** (`manifest.json`): PWA metadata for Add to Home Screen.
- **Icons**: `icon-192.png` and `icon-512.png` — generated from Python script, simple green cup.

## Deployment

GitHub Pages from `main` branch. Every push to `main` auto-deploys to `https://leaniz.github.io/cuaderno/`.

```
git add -A && git commit -m "..." && git push
```

That's the entire deploy process. Wait ~60s for Pages to build.

## After Editing index.html

1. Bump `APP_VERSION` in the script (search for `const APP_VERSION=`)
2. Bump `CACHE` version in `sw.js` (e.g., `cuaderno-v3` → `cuaderno-v4`)
3. Commit and push

If you forget to bump the SW cache, users won't get the update until the browser happens to check (up to 24h). The version bump is what triggers the "Nueva versión disponible" banner.

## Key Conventions

- All UI text is in **Spanish** (the user is Spanish-speaking)
- Scores are 0–1 in 0.1 steps, displayed with comma decimal (`0,6` not `0.6`)
- The radar enforces **blind scoring**: previous radars and bag notes are hidden until the user saves
- `armed()` is a double-tap confirmation pattern (replacement for `confirm()` which is blocked in some contexts)
- The app must work **offline** — the timer runs mid-brew with no network. Never add external CDN dependencies.
- Keep it a **single HTML file** with inline everything. No external CSS, no external JS, no imports.

## Sync

Cloud backup uses GitHub Gist API. The app stores a personal access token (Gist-scoped) and a Gist ID in `cuaderno-sync` localStorage key. On connect, it searches for an existing "Cuaderno" Gist before creating a new one.

## Owner

Javier — uses this daily for V60/AeroPress brews. The app is also maintained from the `/Users/javier/Documents/Cafe` knowledge base repo where the original artifact version lives at `output/tools/cuaderno-brew-app.html`. This repo is the production version.

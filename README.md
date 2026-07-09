# Cuaderno ☕

A personal coffee brew logger — guided pour timer, blind tasting radar, and cloud backup.

**Live app**: [leaniz.github.io/cuaderno](https://leaniz.github.io/cuaderno/)

## Features

- **Guided pour timer** with recipe library (Hoffmann, Tetsu Kasuya 4:6, AeroPress, French press, continuous pour)
- **8-axis blind tasting radar** — previous scores and bag notes hidden until you save
- **Bean & equipment registry** with automatic days-post-roast tracking
- **Prediction locking** — write what you expect before brewing, review after
- **External tasting log** for cafeteria visits and drip bags
- **Cloud sync** via GitHub Gist (optional — works fully offline)
- **PWA** — install on your phone's home screen, works offline mid-brew

## Install

1. Open [leaniz.github.io/cuaderno](https://leaniz.github.io/cuaderno/) in Safari (iOS) or Chrome (Android)
2. Share → Add to Home Screen
3. Done — it's an app now

## Cloud Sync Setup

1. Create a [GitHub fine-grained token](https://github.com/settings/tokens?type=beta) with Gist read/write permission
2. In the app: Historial → Sincronización → paste token → Conectar
3. Tap "Enviar a la nube" after each session

## Deploy Status

Every push to `main` auto-deploys via GitHub Pages. Check build progress at [Actions](https://github.com/Leaniz/cuaderno/actions).

## Tech

Single HTML file, no build step, no dependencies. Vanilla JS, inline CSS, service worker for offline caching. Data lives in localStorage with optional Gist backup.

## License

Personal project. Not currently licensed for redistribution.

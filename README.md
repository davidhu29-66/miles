# Mileage Logbook

A standalone version of the mileage-tracking app, set up to deploy to Vercel (or any static host).

## What was fixed vs. dropping the raw component into a repo

1. **Tailwind CSS is now actually configured** (`tailwind.config.js`, `postcss.config.js`, `src/index.css`)
   so the dark theme, spacing, and colors render — previously nothing was styled at all.
2. **`window.storage` is polyfilled** (`src/storagePolyfill.js`) using real `localStorage`, since the
   original `window.storage` API only exists inside Claude's sandbox. The app component itself
   (`src/MileageLogger.jsx`) is untouched — same file Claude gave you.

## Run locally

```bash
npm install
npm run dev
```

## Deploy to Vercel

Push this folder to GitHub, then import the repo in Vercel. It auto-detects Vite —
no extra config needed. Build command: `npm run build`, output directory: `dist`.

## Data storage — read this

Trips are saved in your browser's `localStorage`, keyed to whichever device/browser you use it on.
That means:
- Data does **not** sync between your phone and laptop, or across browsers.
- Clearing site data/cache in that browser will erase your trips.
- It's fine for single-device daily use, but if you want it backed up or synced across devices,
  that needs a real backend (e.g. a small database + login) — happy to help with that next if
  you want it.

Use the **Export CSV** button in the Summary tab regularly to keep a backup outside the browser.

## Updating the app later

If Claude gives you an updated `MileageLogger.jsx` in the future, you can just replace
`src/MileageLogger.jsx` with the new version — nothing else needs to change.

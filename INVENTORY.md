# Inventory — Bobin Maker

This document lists the main files, embedded dependencies, external assets, and persistence keys used by the Bobin Maker app.

## Files

- `index.html`
  - Single-file application (HTML + CSS + JS)
- `vendor/three.r155.min.js`
  - Local Three.js build (r155)
- `vendor/tabler-icons-webfont/`
  - Local Tabler Icons webfont (CSS + fonts + MIT license text)
- `fonts/`
  - Local Poppins subset (Latin) for offline museum/workshop setups (`.woff2` + OFL license file)
- `img/The_Great_Wave_off_Kanagawa.jpg`
  - Local image asset (offline-friendly fallback)

## External Resources (network)

- Three.js fallback (only if the local vendor file is missing)
  - `https://unpkg.com/three@0.155.0/build/three.min.js`
- Wave image fallback (only if the local file is missing)
  - `https://upload.wikimedia.org/wikipedia/commons/0/0a/The_Great_Wave_off_Kanagawa.jpg`

## Embedded Dependencies

- Three.js r155
  - Loaded from `vendor/three.r155.min.js` (no bundler). A CDN fallback is injected at runtime if missing.

## Browser Storage

- `localStorage`
  - Key: `waraiguma_mypal`
  - Content: JSON array with up to 8 saved entries
    - Each entry stores `hex` and a snapshot of the current settings (`params`) to restore bobbin geometry/material along with the color.
  - Access: via a small `Store` wrapper in `index.html` to avoid crashes in private mode / quota / eviction scenarios.

## Exports / Outputs

- PNG export
  - High-resolution export that includes all saved bobbins.
- USDZ export
  - Intended for AR Quick Look on iPhone/iPad.
  - Includes embedded procedural textures (diffuse + normal) for a closer match to the live look.

## Notes for GitHub Publication

- License: see `LICENSE` and `NOTICE.md`.
- Consider pinning the external CDN versions and documenting any offline limitations.
- Layout/responsive: the app uses `ResizeObserver` (header, dock, and canvas host) to keep CSS vars and the WebGL renderer in sync during responsive reflow and panel transitions.

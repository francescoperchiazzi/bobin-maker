# Waraiguma · Bobin Maker — Technical Notes (for GitHub)

This file exists to keep a small, explicit record of what has been hardened (done) and what is intentionally left as future work. It complements the README (story + intent).

Last verified: 2026‑06‑06.

## Snapshot (as shipped)

- Single static page app: `index.html` contains HTML + CSS + JS (no build step).
- Three.js: local `vendor/three.r155.min.js` (r155). If missing, the app can load a pinned CDN fallback (`https://unpkg.com/three@0.155.0/...`) after waiting for `window.THREE`.
- Storage: “My palette” persisted via `localStorage` key `waraiguma_mypal`, accessed through a safe `Store` wrapper.
- i18n: 4 languages (IT/EN/FR/JA) via `TR` + `[data-t]` updates.
- Offline fonts: local Poppins subset (Latin, 400/600/700/800) via `@font-face` under `fonts/`.

## Hardened (implemented)

- Startup reliability: guarded init (`ensureThree()`), loader message + localized error if Three.js cannot be loaded.
- WebGL resilience: `webglcontextlost` / `webglcontextrestored` handled with a rebuild.
- GPU hygiene: full disposal on rebuild for Mesh/Points (Lamé glitter particles) to prevent VRAM leaks.
- Export PNG: offscreen sRGB, same lighting (incl. rim), UI yielding during grid render, final output size clamped (iOS 4096 / others 8192), localized error if canvas allocation fails.
- Export UX: during PNG generation (download/share), the WebGL canvas is hidden behind the loader to avoid showing intermediate rebuilds.
- Interaction quality: touch drag state is stable; inertia/colour transitions are delta‑time normalized (60/120Hz); rebuild requests are queued (no dropped last value).
- Resize stability (Kids/Pro toggle): canvas resize requests are queued and applied in the render loop to avoid blank frames during the panel transition.
- Touch usability (iOS/iPadOS): larger range slider thumbs + extra vertical spacing to avoid accidental multi-control touches.
- i18n/a11y cleanup: roughness wording fixed; JP “Wave” terminology fixed; kids pick/select differentiated in JA; key aria/title attributes localized (incl. dynamic remove-from-palette labels); localized PNG-generation loader message in 4 languages.
- Offline readiness: Tabler Icons webfont is vendored locally (no CDN dependency for icons).
- Safari/iPad visual stability: palette swatches rendering hardened to avoid compositing artifacts during add/remove interactions.
- Licensing/docs: `LICENSE` (MIT) + `NOTICE.md` present; Wave image terms checked and documented as PD‑Art / Public Domain Mark 1.0 with jurisdiction notes.

## Known limitations (intentional)

- USDZ (AR): Bouclé fuzz and Lamé glitter are approximated via embedded procedural textures (diffuse + normal). They are not exported as true geometry/particles.

## Open / future work (optional)

- Context restore continuity: persist the current bobbin state before heavy exports and restore it after a WebGL context restore, so users never lose progress.
- Maintainability refactor (no build step): split `index.html` into `css/` + `js/` (and optionally normalize mixed IT/EN identifiers while doing so).

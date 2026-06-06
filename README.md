# Waraiguma · Bobin Maker

A small spatial color-play tool created for children.

## Why This Project Exists

Waraiguma Bobin Maker was created during the long weekend of **2 June 2026** by Francesco Perchiazzi as a personal contribution to **Il Mare come Artigiano**, an educational workshop for children held at the **Naples Fashion Museum**.

The workshop invited six-year-old children to explore colors, patterns, weaving, imagination, and textile culture through playful experimentation inspired by the educational philosophy of **Bruno Munari**.

While preparing support activities for the workshop, a simple question emerged:

How can a child explore colors through a digital object without first having to learn software?

Bobin Maker is an attempt to answer that question.

Rather than reproducing a professional design tool, the project aims to create an immediate relationship between gesture, color, and imagination. Children can paint a yarn bobbin, create simple palettes, save their favorite combinations, and observe how colors behave on a three-dimensional object.

The experience is intentionally lightweight. There are no accounts, no databases, no complex workflows, and no learning curve.

Just colors, experimentation, and curiosity.

## A Personal Note

This repository is not the result of a commercial commission.

It was developed as a personal weekend project by Francesco Perchiazzi, designer, researcher, and adjunct professor of Graphic Design at the University of Naples Federico II.

The initial concept was developed through rapid prototyping and Vibe Coding methodologies, using AI-assisted development tools and continuous experimentation.

Part of the interaction design was informally validated with Francesco’s daughter Celeste, whose reactions helped identify which interactions felt natural, understandable, and engaging for young children.

For this reason, the project should be viewed more as a design experiment than as a software product.

It is a small exploration of how digital tools can support creativity, perception, and learning in early childhood.

## Design Principles

The project follows five simple principles:

### 1. Immediate Understanding

A child should understand the interface without instructions.

### 2. Play Before Function

Exploration comes before productivity.

### 3. Physical Metaphors

The bobbin is not an abstract UI element. It is a familiar object connected to textile culture.

### 4. Spatial Thinking

Colors are applied to a three-dimensional object rather than a flat swatch. The object becomes a cognitive bridge between imagination and materiality.

### 5. Low Friction

No login. No onboarding. No configuration. No account creation.

## Educational Context

This project was originally created to support:

- color recognition
- palette creation
- visual experimentation
- pattern thinking
- textile education
- creative confidence

The software does not attempt to teach design. Instead, it creates conditions for children to discover design principles through play.

## Features (Secondary)

- 3D bobbin preview with immediate visual feedback
- Two UI modes: Kids / Pro
- Built-in palettes (Kids + Wave)
- Personal palette saved locally (up to 8 saved bobbins, `localStorage` key: `waraiguma_mypal`)
- PNG export (single bobbin or saved palette grid)
- USDZ export for AR on iPhone/iPad (with embedded procedural textures)

## Run Locally

This app is a static web page with no build step.

From `apps/bobinmaker`:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080/`.

## Project Structure

- [index.html](./index.html): the application (HTML/CSS/JS)
- [vendor/three.r155.min.js](./vendor/three.r155.min.js): local Three.js build (r155)
- [vendor/tabler-icons-webfont/](./vendor/tabler-icons-webfont/): local Tabler Icons webfont (CSS + fonts, MIT)
- [fonts/](./fonts/): local Poppins subset for offline setups (OFL)
- [img/The_Great_Wave_off_Kanagawa.jpg](./img/The_Great_Wave_off_Kanagawa.jpg): Wave image local asset

## Credits & Thanks

- Waraiguma · Il Mare come Artigiano — Naples Fashion Museum · 9–12 June 2026 · Lab by Paola Maddaluno
- About the project: “The Sea as Craftsman” is a creative workshop for children promoted by the City of Naples, exploring how fabrics are conceived and made. Six-year-olds draw on tablets and weave on hand looms, inspired by Bruno Munari’s lessons.
- Promoted by: City of Naples — Chiara Marciani
- Co-operative: L'Orsa Maggiore — Francesca D'Onofrio
- Venue: Naples Fashion Museum
- Curated by: Paola Maddaluno
- Tech: Vimar 1991 – Chanel Group

## Image Attribution

- Wave image source: https://commons.wikimedia.org/wiki/File:The_Great_Wave_off_Kanagawa.jpg
- Per the Wikimedia Commons file page, this is described as PD‑Art / Public Domain Mark 1.0 (with jurisdiction notes). Refer to the page for the authoritative terms.

## License

- Code: MIT License — see [LICENSE](./LICENSE).
- Third‑party assets (image/fonts/icons): see [NOTICE](./NOTICE.md).

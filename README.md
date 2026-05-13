# Mission Map — Prototype v1

Mobile-first prototype of the Mission Map home screen, with a built-in editor for
configuring the island roster, ordering and state from the browser. No build, no
server — plain HTML/CSS/JS opens straight from `file://`.

## Scope

- **Map tab** — vertical zig-zag of islands (= missions), connected by a hand-drawn
  trail, on a CSS-only parallax sky. Tap on an island runs a visible 280 ms press
  animation, then navigates to the existing Mission Page prototype (`../mission-page/mission-page-v3.html`).
- **Editor tab** — upload PNG islands, edit titles and lesson counts, drag to
  reorder, set state per mission (done / current / available / locked), delete
  with a cross. Changes immediately reflect in the Map tab.
- **Header (sticky)** — pill with active plan title + chevron, avatar circle on
  the right, amber progress bar with `done / total` counter. Pill tap is a no-op
  in v1 — a static stub of the plan switcher.

## Intentional divergence from the reviewed spec

The reviewed spec at `docs/product-specs/2026-04-mission-map.md` calls for DS
Mission Node components, not illustrated PNG islands, and a fixed 12-mission
shape. This prototype deliberately diverges to test the "island map" feel.
The spec is NOT updated — reconciliation with the design system happens later.

Out of v1: plan switcher dropdown, Expert-lock modal, profile entry, Day-0
fallback wiring, cross-session scroll restore.

## Data

Everything lives in `localStorage` under the key `missionMap.missions`.
Uploaded PNGs are auto-resized to ≤512 px on the longest side and stored as
base64 data URLs — this keeps the whole roster well under the localStorage
quota even for 30+ islands.

## Files

```
mission-map/
├── README.md          — this file
├── index.html         — markup + tab structure
├── styles.css         — all CSS (header, tabs, map, editor, parallax)
├── app.js             — data layer, render, drag-reorder, press animation
└── assets/
    └── islands/       — optional reserve for static PNG drops (not used by v1
                         editor flow, which stores everything in localStorage)
```

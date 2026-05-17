# assets/ — bundled design resources

Self-contained, offline-ready libraries used by `preview.html` and the
`color-palettes` skill. Licenses summarized in `../THIRD_PARTY_LICENSES.md`.

```
assets/
├── fonts/        OFL 1.1 — 10 families, woff2 + fonts.css (@font-face)
├── icons/lucide/ ISC     — 1960 icons: sprite.svg, icons/*.svg, index.json, tags.json
└── patterns/     CC0     — 16 tileable SVG patterns + ornaments/, patterns.css, index.json
```

### Fonts
`<link rel="stylesheet" href="assets/fonts/fonts.css">` then use the
family names (Fraunces, Inter, Playfair Display, Source Serif 4, Newsreader,
Spectral, Space Grotesk, IBM Plex Mono, Noto Serif SC, Noto Sans SC).
No network needed.

### Icons (Lucide)
Sprite: `<svg><use href="assets/icons/lucide/sprite.svg#camera"/></svg>`.
All names in `icons/index.json`; search keywords in `icons/tags.json`.
SVGs use `stroke="currentColor"`.

### Patterns
`background-image:url(assets/patterns/grid.svg)` — `currentColor`, tune with
`color` + `opacity`. Names in `patterns/index.json`. Decorative dividers/marks
in `patterns/ornaments/` (incl. `asterisk.svg`, the ✻ motif).

---
role: dev
owner: gfabr
status: active
---

# Dev

## Decisions

- **2026-03-27 — Font stack: Literata + Shippori Mincho.** Literata (variable, optical size axis) for EN/FR body. Shippori Mincho for JA body. Google Fonts CDN for now. `font-display: swap` per prompt. [[arch]]

- **2026-03-27 — View state via JS, single HTML file.** Two views: landing (default) and reader (per story). URL hash for story navigation (`#story-1`, etc.) so back button works. No framework. [[arch]]

## Dead Ends

_None yet._

## Lessons

_None yet._

## Open Questions

- `writing-mode: vertical-rl` container: needs `max-height` constraint (analog to `max-width` for horizontal). Use viewport height minus padding? Or a fixed value?
- Vertical scroll for `vertical-rl` content is actually horizontal swipe/scroll on the page. Need `overflow-x: auto` on the container. Test on mobile Safari especially.
- French text cleanup: OCR artifacts in La Parure (e.g. `I'indignaient`). Clean before embedding.
- Story content embedding: inline in HTML, or in `<template>` tags? Inline is simpler and works with JS-off.

## Assumptions

- Browser target: modern evergreen (Chrome/Firefox/Safari/Edge). No IE11.
- `dvh` units available (Safari 15.4+, Chrome 108+).
- `word-break: auto-phrase` is progressive enhancement (Chrome 119+ only).
- `writing-mode: vertical-rl` well-supported (all modern browsers since 2017+).

## Dependencies

- [[arch]] for layout decisions
- [[ux]] for interaction patterns
- [[qa]] for acceptance criteria verification

## Session Log

2026-03-27 — Font stack, view state model, vertical writing considerations
2026-03-27 — INIT — role created

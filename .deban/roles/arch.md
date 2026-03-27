---
role: arch
owner: gfabr
status: active
---

# Arch

## Decisions

- **2026-03-27 — Landing page + story reader model.** Original prompt assumed 200-word stories in viewport-sized sections. Actual content is full-length (7K words EN, 2.7K words FR, 800 chars JA short, 7K chars JA long). Architecture shifts from "four viewport slides" to "landing page with story cards → full-scroll story reader." Still single HTML file — JS manages view state. Alternatives considered: (a) keep viewport-per-story with internal scroll — rejected because mixing horizontal swipe nav with vertical scroll is a UX minefield, especially on mobile. (b) separate HTML files — rejected because single-file constraint is in the brief. [[ux]] [[dev]]

- **2026-03-27 — Vertical writing mode for 火を焚く.** Japanese translation of To Build a Fire uses `writing-mode: vertical-rl`. The gourmet satire stays horizontal (contemporary comedic tone suits 横書き). This makes the project a real typography exercise — it now tests two fundamentally different layout axes. [[dev]] [[ux]]

- **2026-03-27 — Font upgrade: Literata + Shippori Mincho.** Literata replaces Lora: optical size axis adapts to body vs display automatically, designed for e-readers. Shippori Mincho replaces Noto Serif JP: higher contrast, more elegant, better for literary content. Both on Google Fonts. Google Fonts CDN retained for now — self-hosting woff2 alongside is impractical in a single-file constraint (base64 inline would balloon filesize, especially JA font). Flag for future: self-host when expanding beyond single-file. [[dev]]

- **2026-03-27 — External content loading via fetch().** Stories remain as `.md` files, loaded at runtime. A JSON manifest (`stories.json`) defines order, metadata, writing mode. HTML stays content-free — pure presentation + logic. Trade-off: requires HTTP server (no `file://` due to CORS). Acceptable for a dev/demo context. Alternatives rejected: (a) inline all stories in HTML — not scalable, bloats file, mixes concerns. (b) `<template>` tags — still inline, same problem. [[dev]] [[pm]]

## Dead Ends

_None yet._

## Lessons

_None yet._

## Open Questions

- Vertical scroll container for stories: should the landing page fully disappear (replaced by story view) or remain as a back-navigation layer?
- Vertical writing `writing-mode: vertical-rl` needs `max-height` (not `max-width`) for column constraint. What's the right value? Full viewport height minus padding? Reader controls height via scroll.
- Reading progress indicator for long stories? Or does that violate minimalism? Lean toward no.

## Assumptions

- No SSR, no hydration — pure static HTML.
- Performance budget is effectively zero JS frameworks = fast by default.
- Google Fonts CDN acceptable for now; self-hosting deferred.

## Dependencies

- [[dev]] for implementation
- [[ux]] for interaction model

## Session Log

2026-03-27 — Revised architecture: landing page model, vertical JA, font upgrade
2026-03-27 — INIT — role created

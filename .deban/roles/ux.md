---
role: ux
owner: gfabr
status: active
---

# UX

## Decisions

- **2026-03-27 — Landing page as navigation hub.** Clean grid of story cards. Title only (language inferred from title text). "+" button per card expands to show a one-line excerpt. No reading time for MVP (keep for later). [[arch]] [[pm]]

- **2026-03-27 — Full-scroll reading for stories.** Stories scroll vertically (horizontal for EN/FR/JA横書き). 火を焚く uses `writing-mode: vertical-rl` — reader scrolls horizontally (right to left). [[arch]]

- **2026-03-27 — Back navigation: dual mode.** Desktop: minimal arrow top-left. Mobile: swipe-from-edge (right edge → back to landing). Arrow hidden on mobile to keep the reading surface clean. [[dev]]

## Dead Ends

_None yet._

## Lessons

_None yet._

## Open Questions

- Vertical Japanese reading (火を焚く): horizontal scroll direction (right-to-left) is native for JA readers but unfamiliar to others. Any affordance needed? Lean toward no — the reader self-selects by choosing a Japanese story.
- "+" expand interaction: tap toggles? Or hover on desktop, tap on mobile? Keep it simple — tap/click toggles everywhere.
- Reading position memory: deferred. Always start from top for now.

## Assumptions

- Users understand card-based navigation from modern web.
- Title alone is sufficient to signal language (e.g. "火を焚く" is self-evidently Japanese).
- No accessibility audit beyond WCAG contrast and touch targets.

## Dependencies

- [[pm]] for scope decisions
- [[dev]] for implementation feasibility
- [[arch]] for layout model

## Session Log

2026-03-27 — Finalized: title-only cards with "+" excerpt, dual back-nav, no reading time yet
2026-03-27 — INIT — role created

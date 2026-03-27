---
project: MoFoWeTypography — Minimalist Short-Stories Reader
brief: >
  Single HTML file, no frameworks, no build step. Renders four public-domain/original
  stories (EN, FR, JA horizontal, JA vertical) with research-grounded typography.
  Landing page → full-scroll reader. Typography exercise first, web exercise second.
  Expanding beyond four stories later.
mode: solo
owner: gfabr
created: 2026-03-27
stale_threshold_days: 30
---

# MoFoWeTypography

## Active Roles

| Role | Owner | Status |
|------|-------|--------|
| [[dev]] | gfabr | active |
| [[arch]] | gfabr | active |
| [[pm]] | gfabr | active |
| [[ux]] | gfabr | active |
| [[qa]] | gfabr | active |
| [[devops]] | gfabr | dormant |

## Key Decisions

- Landing page + full-scroll reader model (not viewport slides)
- Vertical writing mode (`vertical-rl`) for 火を焚く; horizontal for gourmet story
- Fonts: Literata (Latin) + Shippori Mincho (JA) — Google Fonts CDN for now
- Four stories as MVP test set; architecture accommodates expansion

## Open Questions

- French text OCR cleanup needed (La Parure artifacts)
- Vertical-rl scroll UX on mobile needs testing
- Self-hosting fonts deferred until multi-file expansion

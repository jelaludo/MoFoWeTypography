---
role: pm
owner: gfabr
status: active
---

# PM

## Decisions

- **2026-03-27 — Resolved initial challenges.** User responses:
  1. Story length: only the JA gourmet story is short. EN and JA translation are ~7K words each. FR is ~2.7K words. Typography stress-testing is real.
  2. Four stories is the test set — will expand later. Architecture must accommodate growth.
  3. Landing page added for discoverability — solves the "swipe is undiscoverable" problem.
  4. Self-host fonts preferred. Using typography skill picks: Literata + Shippori Mincho. Google Fonts CDN for now (single-file constraint), self-hosting deferred.
  5. Both vertical and horizontal Japanese writing modes. 火を焚く gets `writing-mode: vertical-rl`, gourmet story stays horizontal.

## Dead Ends

_None yet._

## Lessons

_None yet._

## Open Questions — Remaining

1. **Story expansion model.** "Will expand later" — does this mean more HTML sections added manually, or should the architecture support loading stories from external files / a manifest? For now: hardcoded, but keep structure clean enough to extend.

2. **French story choice.** La Parure (Maupassant) is 2.7K words — solid medium-length test. But the OCR has artifacts (e.g. line 8: `I'indignaient` should be `l'indignaient`). Text cleanup needed before embedding.

## Assumptions

- Target audience: typography-literate developers/designers evaluating typographic quality.
- Not a production product — a demonstration piece, but expanding.
- No accessibility requirements beyond WCAG contrast and ARIA nav.
- Four stories is the MVP; architecture should not preclude adding more.

## Dependencies

- [[ux]] for interaction discoverability
- [[qa]] for acceptance criteria
- [[arch]] for expansion model

## Session Log

2026-03-27 — Resolved 5/5 initial challenges, 2 new questions opened
2026-03-27 — INIT — role created, 5 assumptions challenged

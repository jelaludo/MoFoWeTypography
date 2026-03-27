---
role: qa
owner: gfabr
status: active
---

# QA

## Decisions

_None yet._

## Dead Ends

_None yet._

## Lessons

_None yet._

## Open Questions

- How to verify CPL count? Manual inspection or automated tooling? `ch` units are font-dependent — actual character count per line varies.
- Contrast verification: computed from hex values in CSS, but actual rendered contrast depends on font weight and anti-aliasing. Programmatic check sufficient?
- Japanese kinsoku testing: need specific test strings with problematic characters (opening brackets at line end, closing brackets at line start, prolonged sound marks).
- Swipe threshold (50px): tested on which devices? 50px on a 320px-wide phone is ~15% of screen width — may feel unresponsive. On a tablet, 50px is trivial — may trigger accidentally.

## Assumptions

- Testing is manual/visual — no automated test suite for a single HTML file.
- Browser testing: Chrome + Safari minimum. Firefox nice-to-have.

## Dependencies

- [[dev]] for implementation to test
- [[pm]] for acceptance criteria ownership

## Session Log

2026-03-27 — INIT — role created

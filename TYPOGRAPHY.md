# Typography

Project-specific typography decisions and audit history.

---

## Current State

| Property | Value | Status |
|----------|-------|--------|
| Body CPL | `min(90vw, 65ch)` Latin / `min(90vw, 38em)` Japanese | planned |
| Body font size | `clamp(16px, 1.1vw + 14px, 18px)` | planned |
| Body line-height | 1.5 Latin / 1.7 Japanese | planned |
| Light contrast | `#1a1a1a` on `#f5f5f5` (~12.6:1) | planned |
| Dark mode | `#e8e8e8` on `#121212` (~14.4:1) | planned |
| Type scale | 1.25 major third, 7 sizes defined | planned |
| Mobile viewport | `<meta name="viewport" ...>` | planned |
| Touch targets | ≥44px on nav dots | planned |
| Japanese support | full — `lang="ja"`, kinsoku, Mincho stack, no italics | planned |
| Token file | inline `<style>` in `reading.html` | planned |
| Font families | Literata (Latin serif) / Shippori Mincho (Japanese) | planned |
| Font loading | Google Fonts CDN, `font-display: swap` | planned |
| Vertical writing | `writing-mode: vertical-rl` for 火を焚く | planned |

## Session Log

### 2026-03-27 — Generative (Scaffold)

**Mode:** Generative
**Surfaces touched:** project planning — no CSS written yet

#### Before

Greenfield — no prior typography. Prompt file (`prompt-reading-website.md`) defines all typographic rules in advance. Four reference story files exist (full-length public domain works) but the prompt calls for original 180–250 word micro-stories.

#### Decisions

| Decision | Value chosen | Basis |
|----------|-------------|-------|
| Latin body CPL | 65ch via `min(90vw, 65ch)` | Skill §1.1 — Baymard sweet spot, Bringhurst 45–75 |
| Japanese body CPL | 38em via `min(90vw, 38em)` | Skill §3.1 — `em` not `ch` for CJK |
| Body font size | `clamp(16px, 1.1vw + 14px, 18px)` | Skill §1.2 — 16px mobile floor, 18px desktop target |
| Latin line-height | 1.5 at 65ch column | Skill §1.3 — matched to column width |
| Japanese line-height | 1.7 | Skill §3.1 — no ascenders/descenders in kanji |
| Light text color | `#1a1a1a` on `#f5f5f5` | Skill §1.5 — softened, not pure black/white |
| Dark text color | `#e8e8e8` on `#121212` | Skill §1.5 — Material dark surface base |
| Latin font | Lora (reading serif) | Prompt spec — variable stroke, comfortable x-height |
| Japanese font | Noto Serif JP (Mincho) | Prompt spec — complete weight coverage, screen legible |
| Font loading | `font-display: swap` | Prompt spec overrides Skill §1.9 (`optional` recommendation) |
| Type scale | 1.25 major third from 16px | Skill §1.4 — standard web UI ratio |
| Japanese text-align | `justify` + `text-align-last: left` | Skill §3.1 — no word spaces = no rivers |
| Japanese kinsoku | `line-break: strict; word-break: keep-all` | Skill §3.1 — JIS X 4051 |
| No italics on JA | enforced | Skill §4 Japanese prohibition #2 |
| No justify on Latin | enforced | Skill §4 Latin prohibition #1 |
| Dark bg | `#121212` never `#000` | Skill §4 Latin prohibition #4 |

#### Violations Found

_N/A — generative mode._

#### After

Project scaffolded. Typography rules documented. No code written yet.

#### Open Items

- Font loading: `swap` (prompt) vs `optional` (skill) — prompt wins, but worth revisiting if FOUT is noticeable with Lora/Noto Serif JP
- Japanese vertical writing (`writing-mode: vertical-rl`) not considered in prompt — flagged as open question
- Mobile line-height: prompt says 1.6, skill says 1.55–1.6 — need to decide if mobile override is worth the complexity
- Existing story files in repo are full-length — not usable as content; original micro-stories needed

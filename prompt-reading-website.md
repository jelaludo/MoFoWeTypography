# Agent Prompt: Minimalist Reading Website

## Mission

Build a single HTML file — no frameworks, no build step, no dependencies except fonts — that renders four short stories with maximum reading comfort on mobile and desktop. The output is one self-contained `.html` file.

This is a typography exercise first, a web exercise second. Every decision must serve the reader. Nothing decorates. Nothing signals effort.

Read the typography skill before writing a single line of CSS.

---

## Typography Rules (Non-Negotiable)

Apply the typography skill in full. The rules below are the binding subset for this build.

### Latin (English, French)

- Column: `max-width: min(90vw, 65ch)` — never wider
- Body font size: `clamp(16px, 1.1vw + 14px, 18px)`
- Line height body: `1.5`
- Line height headings: `1.1`
- Paragraph spacing: `margin-block-start: 1.1em` on `p + p`
- Heading spacing: `margin-block-start: 2em; margin-block-end: 0.5em`
- Text color light: `#1a1a1a` on `#f5f5f5`
- Text color dark: `#e8e8e8` on `#121212`
- Alignment: left — never justify for Latin
- Letter-spacing body: 0 — never add it
- Type scale ratio: 1.25 from 16px base

### Japanese

- Column: `max-width: min(90vw, 38em)` — `em` not `ch`
- Line height: `1.7`
- Letter-spacing: `0.05em`
- Alignment: `justify` with `text-align-last: left`
- Kinsoku: `line-break: strict; word-break: keep-all; overflow-wrap: break-word`
- Headings: `word-break: auto-phrase; letter-spacing: 0; line-height: 1.25`
- Never: `font-style: italic`, `word-break: break-all`, `ch` units for column width
- `lang="ja"` must be on every Japanese content element or its ancestor

### Dark Mode

- Background dark: `#121212` — never `#000000`
- Text dark: `#e8e8e8` — never `#ffffff`
- Respect `prefers-color-scheme` — no manual toggle required
- Surface elevation dark: `#1e1e1e` for any cards or panels

### Mobile

- Viewport meta: `<meta name="viewport" content="width=device-width, initial-scale=1">`
- Font sizes via `clamp()` — no fixed px at specific breakpoints
- Touch targets (nav, any interactive element): minimum `44px` height
- Mobile line-height: `1.6` (slightly higher than desktop `1.5`)

---

## Architecture

**One file.** `index.html` with embedded `<style>` and `<script>`. No external CSS files. No JS frameworks.

Font loading is the only external dependency — use Google Fonts with subsetting. Required fonts:

```html
<!-- Latin: reading serif -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">

<!-- Japanese: system stack preferred, Noto as cross-platform fallback -->
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+JP:wght@400;700&display=swap" rel="stylesheet">
```

Font stacks:
```css
--font-latin:    'Lora', Georgia, serif;
--font-japanese: 'Noto Serif JP', 'Hiragino Mincho ProN', 'ヒラギノ明朝 ProN',
                 'Yu Mincho', '游明朝体', YuMincho, serif;
```

Lora is chosen for Latin because: variable stroke width, comfortable x-height, designed for screen reading, gentle serifs that survive small sizes. It is a reading font, not a display font.

Noto Serif JP for Japanese because: the only free font with complete weight coverage, correct Mincho stroke terminals, designed for screen legibility.

---

## Layout

Full-screen, single-page, story-by-story. Each story occupies its own full viewport section. Navigation between stories is minimal — the reader should feel like turning a page, not using an app.

### Structure

```
[Story 1 — English]
[Story 2 — French]
[Story 3 — Japanese]
[Story 4 — Japanese]
```

### Navigation

- Fixed bottom bar: four dots or minimal indicators, one per story
- Active dot: filled. Inactive: outlined. No labels.
- Keyboard: arrow keys advance/retreat stories
- Touch: swipe left/right (implement with touch events — no library)
- No visible prev/next buttons unless on desktop hover

### Story container

Each story is a full-viewport section (`100dvh`). Content is vertically centered with a slight upward bias (60/40 top/bottom padding rather than 50/50 — optically better for reading).

```css
.story {
  min-height: 100dvh;
  display: grid;
  place-items: start center;
  padding-block: 8vh 12vh;
  padding-inline: max(1.5rem, 5vw);
}
```

The reading column sits inside, constrained by `max-width` rules above.

---

## Content

Write all four stories. Each should be:
- 180–250 words
- Thematically self-contained — begins and ends
- Tonally quiet — no plot twists, no dramatic arc. The prose equivalent of a short walk.
- Written as if it belongs in the typography demo (the writing is also the test)

### Story 1 — English

Title: something spare, one to three words.
Theme: observation. A person noticing something small in ordinary surroundings.

### Story 2 — French

Title: one to three words, French.
Theme: memory — a single recovered detail from the past, held up to the light.
Language register: literary but accessible. Not academic. Not colloquial.

### Story 3 — Japanese (横書き horizontal)

Title: 2–5 characters.
Theme: 間 (ma) — negative space, the pause between things.
Prose: contemporary Japanese. Short sentences. Much is left unsaid.
`lang="ja"` on the containing section.

### Story 4 — Japanese (横書き horizontal)

Title: 2–5 characters.
Theme: 物の哀れ (mono no aware) — the gentle sadness of transience.
Prose: contemporary Japanese. Slightly longer sentences than Story 3.
`lang="ja"` on the containing section.

---

## CSS Token File

Implement all values as CSS custom properties. The token set must include at minimum:

```css
:root {
  /* Typography */
  --font-latin:       'Lora', Georgia, serif;
  --font-japanese:    'Noto Serif JP', 'Hiragino Mincho ProN', serif;
  --size-xs:          0.75rem;
  --size-sm:          0.875rem;
  --size-base:        1rem;
  --size-md:          1.25rem;
  --size-lg:          1.5625rem;
  --size-xl:          1.953rem;
  --size-2xl:         2.441rem;
  --lh-body:          1.5;
  --lh-body-mobile:   1.6;
  --lh-body-ja:       1.7;
  --lh-heading:       1.1;
  --lh-heading-ja:    1.25;
  --ls-body-ja:       0.05em;
  --paragraph-gap:    1.1em;

  /* Color — light */
  --color-text:           #1a1a1a;
  --color-text-secondary: #595959;
  --color-bg:             #f5f5f5;
  --color-surface:        #ffffff;
  --color-dot-active:     #1a1a1a;
  --color-dot-inactive:   transparent;
  --color-dot-border:     #8a8a8a;

  /* Layout */
  --column-latin:   min(90vw, 65ch);
  --column-ja:      min(90vw, 38em);
  --story-pad-top:  8vh;
  --story-pad-bot:  12vh;

  color-scheme: light dark;
}

@media (prefers-color-scheme: dark) {
  :root {
    --color-text:           #e8e8e8;
    --color-text-secondary: #a0a0a0;
    --color-bg:             #121212;
    --color-surface:        #1e1e1e;
    --color-dot-active:     #e8e8e8;
    --color-dot-border:     #606060;
  }
}
```

---

## Interaction Design

Minimal. Purposeful. Nothing that requires explanation.

**Swipe (mobile):**
```js
// Threshold: 50px horizontal displacement
// Ignore if vertical displacement > horizontal (scrolling intent)
// Animate transition: translateX, 300ms ease
```

**Keyboard (desktop):**
- `ArrowRight` or `ArrowDown` → next story
- `ArrowLeft` or `ArrowUp` → previous story
- `1`–`4` → jump to story

**Scroll within a story:**
- Stories with overflow content scroll vertically within their section
- Navigation dots remain fixed

**Story transition animation:**
- Horizontal slide: `transform: translateX(100%)` → `translateX(0)` → `translateX(-100%)`
- Duration: 300ms
- Easing: `cubic-bezier(0.4, 0, 0.2, 1)`
- No fade, no blur, no zoom — translation only

**No loading states, no skeleton screens, no spinners.** Fonts are the only async dependency; use `font-display: swap` and the content is readable from first paint.

---

## HTML Structure

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang overridden per story section -->
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Four Stories</title>
  <!-- font links -->
  <style>/* all CSS here */</style>
</head>
<body>
  <main class="reader">
    <section class="story" lang="en"   data-index="0"> <!-- Story 1 --> </section>
    <section class="story" lang="fr"   data-index="1"> <!-- Story 2 --> </section>
    <section class="story" lang="ja"   data-index="2"> <!-- Story 3 --> </section>
    <section class="story" lang="ja"   data-index="3"> <!-- Story 4 --> </section>
  </main>
  <nav class="story-nav" aria-label="Story navigation">
    <button class="dot active" aria-label="Story 1" data-target="0"></button>
    <button class="dot"        aria-label="Story 2" data-target="1"></button>
    <button class="dot"        aria-label="Story 3" data-target="3"></button>
    <button class="dot"        aria-label="Story 4" data-target="3"></button>
  </nav>
  <script>/* all JS here */</script>
</body>
</html>
```

Each story section contains:
```html
<article class="story-content">
  <header class="story-header">
    <p class="story-number">01</p>      <!-- small, secondary color -->
    <h1 class="story-title">Title</h1>
    <p class="story-lang">English</p>  <!-- language label, secondary color -->
  </header>
  <div class="story-body">
    <p>…</p>
    <!-- paragraphs -->
  </div>
</article>
```

---

## What Not to Build

- No hero image, no background image, no texture
- No sidebar, no header bar, no footer
- No social sharing, no reading time estimate, no word count
- No custom scrollbar styling
- No CSS animations except the story transition
- No hover effects on text
- No color beyond the token set — no accent colors, no highlights
- No border-radius on story containers (flat surfaces only)
- No box shadows
- No JavaScript libraries — vanilla only
- No `!important` declarations
- No inline styles except where dynamically set by JS (transition state)

---

## Acceptance Criteria

Before delivering, verify:

- [ ] Latin body text is constrained to ≤ 65ch on all viewport widths
- [ ] Japanese body text is constrained to ≤ 38em on all viewport widths
- [ ] Latin line-height ≥ 1.5; Japanese ≥ 1.7
- [ ] Body text ≥ 16px at smallest viewport; ≥ 18px at desktop
- [ ] Both light and dark mode render correctly under `prefers-color-scheme`
- [ ] Background is `#f5f5f5` light / `#121212` dark — not pure white/black
- [ ] Text is `#1a1a1a` light / `#e8e8e8` dark — not pure black/white
- [ ] `lang="ja"` is on both Japanese story sections
- [ ] `line-break: strict` and `word-break: keep-all` applied to `:lang(ja)`
- [ ] No `font-style: italic` applied to Japanese content
- [ ] Japanese text uses `text-align: justify` with `text-align-last: left`
- [ ] Story transition is horizontal slide only, 300ms
- [ ] Swipe navigation works (50px threshold, ignores scroll intent)
- [ ] Keyboard navigation works (arrow keys + number keys)
- [ ] Nav dots are touch targets ≥ 44px
- [ ] Viewport meta tag is present
- [ ] Output is a single `.html` file with no external dependencies except Google Fonts
- [ ] Contrast ratio ≥ 4.5:1 for all body text in both modes
- [ ] No justify on English or French text
- [ ] No `ch` units used for Japanese column width

---

## Output

One file: `reading.html`

Deliver it complete. Do not scaffold and ask for confirmation. Do not truncate the stories. Do not omit the Japanese content. The file should open in a browser and work without any further intervention.

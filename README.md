# Vera Lune Studio — Design System

> Cinematic luxury. Editorial restraint. Print-ready by default.

This is the brand and design system for **Vera Lune Studio**, a fictional luxury wedding photography and cinema studio. It is a **sanitized, shareable example** — a demonstration of how to build a professional, reusable document-generation system in Claude Design. Every name, contact detail, client, and figure here is invented; nothing identifies a real business or person.

The aesthetic target is **Vogue editorial × fine-art wedding cinema**. Every artifact made under this system should look like it could be torn from a glossy magazine or printed on heavy stock and handed to a client in a linen folio.

The primary deliverable this system supports is the **client investment guide PDF** — generated per-client from a structured text input.

> New here? Read [HOW_THIS_WAS_BUILT.md](HOW_THIS_WAS_BUILT.md) for the end-to-end method.

---

## Index

| File / folder | Purpose |
|---|---|
| `README.md` | This file — brand, content, visual foundations, iconography. |
| `HOW_THIS_WAS_BUILT.md` | The Claude Design workflow that produced this system, step by step. |
| `colors_and_type.css` | Design tokens — colors, typography, spacing, motion, semantic element styles. |
| `SKILL.md` | Agent-skill manifest. Use this folder as a portable design skill. |
| `fonts/` | Font notes (currently Google Fonts CDN — see Visual Foundations). |
| `assets/` | Logos and marks (type-set placeholders). |
| `templates/` | Client-facing PDF templates — the 6-page investment guide lives here. |
| `templates/investment_guide.html` | The investment guide PDF master, ready to print to PDF or save. |
| `templates/investment_guide_amara_and_daniel.html` | A filled, personalized example. |
| `templates/CLIENT_DATA_TEMPLATE.txt` | Plain-text fill-in-the-blanks template for per-client generation. |
| `templates/INSTRUCTIONS.md` | How to feed client data and regenerate a personalized guide. |

---

## Brand brief

This system was authored from a short brand brief — the kind of thing a real studio would hand off to a designer.

- **Palette** — `#0A0A0A` deep black, `#C9A96E` champagne gold, `#FAF8F5` warm white, `#2C2C2C` soft charcoal.
- **Type** — Cormorant Garamond (headings), Montserrat Light (body).
- **Visual rules** — full-bleed photography, generous white space, thin gold rule lines, no gradients, no clipart.
- **Tone** — Vogue editorial × fine-art wedding cinema.
- **Tagline** — *Capturing life's most important milestones with cinematic artistry and quiet attention to detail.*
- **Stats** — illustrative placeholders (300+ weddings, 20 countries, 15 years). Replace with real numbers if you adapt this.

> The logo files in `assets/` are **placeholders set in the brand type**. Replace them in place to update every consumer of the system. All contact details use reserved, non-routable values (`veralune.example`, `+1 · 555 · 0142`) so the example is safe to share.

---

## Content fundamentals

Copy under this system follows magazine voice rather than salesy or app-style. The studio is a maker, the client is the subject — never "the user."

**Vibe.** Quiet authority. The studio does not need to shout. Sentences are short and declarative; paragraphs breathe; blocks of body copy rarely exceed three lines on a page.

**Voice.** First person plural for the studio (*we, our*). Second person for the client (*you, your day*). Never "users," "customers," "leads," or any product-y noun.

**Casing.**
- **Titles & section openers** — Title Case in the serif, *italic* for the most important moment on a page.
- **Eyebrows / labels** — UPPERCASE with `0.32em` tracking, sans, 10.5px. These mark the page or section like a magazine kicker.
- **Small caps** — used for client attribution under quotes (e.g. `— ISABEL & MATEO, THE MARIVELLE`).
- **Body** — sentence case. Always.

**Punctuation.**
- **Em dashes** are the studio's signature punctuation — used liberally to set off a clause without breaking flow.
- **Ampersands** are welcome (*Couple & Cinema*, *Investment & Next Steps*) — they read as editorial.
- **Oxford comma**, always.
- **No exclamation marks.** Ever. They cheapen.

**Numerals.**
- Spell out one through nine in body. Use figures for ten and up, all stat callouts, all prices, all dates.
- Stats are paired with a single uppercase word (`300 WEDDINGS`, `20 COUNTRIES`, `15 YEARS`).

**Emoji & exclamatory tropes — none.** No emoji, no decoration, no all-caps headlines for excitement, no marketing exclamations. Restraint is the brand.

---

## Visual foundations

The system rests on five rules. Break any of them and it will stop looking like Vera Lune Studio.

### 1 — Photography is the design

Imagery is **full-bleed by default**. The page is the photograph; the type sits on top of, beside, or under it but never inside a frame around it. Editorial layouts use one large image as the dominant element, with other images smaller and used as counterpoint.

- **Color of imagery** — warm, slightly desaturated, filmic. Skin tones true, whites warm, blacks deep but never crushed. Subtle grain is welcome — heavy filters are not. Never blue-shifted, never HDR.
- **Composition** — negative space respected. Subjects often placed off-center; lots of room for type to breathe over the image.
- **Treatment on top of type** — when type sits on imagery, use a soft inner vignette (`--vl-shadow-vignette`) to seat the text. Never solid scrims, never black bars.

> In this sanitized example, photographs are shown as elegant hairline placeholders so the files render fully offline. Drop a real image URL into a `.photo` / `.left` / `.thumb` background to fill them.

### 2 — Generous white space

The warm white (`#FAF8F5`) is a primary design element, not "the background." Pages routinely allocate **40–60%** of their area to empty warm white. Margins are print-scale (96px+ on screen, 0.75in+ on paper) — never tight.

### 3 — Gold appears in lines and small letters, never in fields

Champagne gold (`#C9A96E`) is **accent only**:
- Thin **rule lines** (1px, 32–56px wide for short rules; full-width for separators).
- **Eyebrow text and prices** when something needs to feel precious.
- **Small caps attribution** under pull quotes.

Gold is **never** used as a background fill, never as a button background by default (only on hover for the primary CTA), never on imagery, never as a gradient. There are no gradients at all in this system. Subtle photographic vignettes are the one and only exception.

### 4 — Sharp corners, hairline rules, no shadows

This is print, not glassmorphism. Corners are 0–2px. Cards have no drop shadows — they're separated by gold or hairline neutral rules. The single shadow exception is the soft inner vignette on photographs.

| Surface | Radius | Border / Rule | Shadow |
|---|---|---|---|
| Page section | `0` | Gold or neutral hairline above/below | None |
| Photograph | `0` | None | Soft inner vignette only |
| Card / panel | `0–2px` | 1px hairline `--vl-rule-neutral` | None |
| Button | `0` | 1px solid currentColor | None |
| Tag / chip | `999px` (pill) | 1px hairline | None |

### 5 — Motion is cinematic, not bouncy

Animations are **fades and slow reveals**. Never bounces, never elastic curves, never spring physics.

- **Easing** — `cubic-bezier(0.32, 0.08, 0.24, 1)` for UI; `cubic-bezier(0.16, 1, 0.3, 1)` for hero reveals.
- **Durations** — 180ms (micro), 320ms (UI), 640ms (page-level), 1200ms (cinematic image reveals).
- **Hover** — color shift only, no transform. Imagery may scale 1.02× over 1.2s on hero hover (cinema-slow).
- **Press** — opacity dip to 0.85, no scale.

### Typography in detail

| Use | Family | Weight | Style | Size | Tracking |
|---|---|---|---|---|---|
| Cover display | Cormorant Garamond | 300 | *italic* | 56–112px | -0.015em |
| H1 | Cormorant Garamond | 300 | roman | 40–72px | -0.005em |
| H2 | Cormorant Garamond | 400 | roman | 28–44px | -0.005em |
| Pull quote | Cormorant Garamond | 300 | *italic* | 28–40px | -0.005em |
| Eyebrow | Montserrat | 400 | UPPERCASE | 10.5px | 0.32em |
| Small caps attribution | Montserrat | 400 | UPPERCASE | 11px | 0.18em |
| Body | Montserrat | **300** (Light) | roman | 15px | 0.005em / leading 1.65 |
| Caption | Montserrat | 300 | UPPERCASE | 11px | 0.06em |
| Price | Cormorant Garamond | 400 | roman | 28px, gold | 0.01em |
| Button label | Montserrat | 400 | UPPERCASE | 11px | 0.22em |

### Color in detail

The four-color core handles 95% of work. Extended neutrals exist only to break ties when two greys would otherwise crash.

| Token | Hex | Use |
|---|---|---|
| `--vl-black` | `#0A0A0A` | Primary text on warm white; full-bleed dark sections |
| `--vl-charcoal` | `#2C2C2C` | Secondary text; dark surfaces less than full black |
| `--vl-gold` | `#C9A96E` | Eyebrows, prices, rule lines, attribution. **Accent only.** |
| `--vl-white` | `#FAF8F5` | Page background. Never pure `#FFF`. |
| `--vl-graphite` | `#4A4A4A` | Tertiary text, captions |
| `--vl-stone` | `#8A8580` | Faint metadata |
| `--vl-bone` | `#F2EEE8` | Subtle warm surface |
| `--vl-pearl` | `#EDE7DD` | Card / panel surface |
| `--vl-gold-soft` | `#D9BE8B` | Hover gold |
| `--vl-gold-deep` | `#A88652` | Press gold (against warm white only) |

### Spacing & layout

- **8pt base.** All spacing snaps to multiples of 4 / 8 / 16 / 24 / 32 / 48 / 64 / 96 / 128 / 160.
- **Print margins.** 0.75–1in (72–96px) on letter; vertical breathing room is always *more* than horizontal.
- **Screen margins.** `clamp(24px, 6vw, 96px)`.
- **Grids.** Editorial 12-column, but most layouts use 1-, 2-, or 3-column splits. Asymmetric splits (1/3 — 2/3) are common.

---

## Iconography

The studio's brand is photographic, not iconographic. Icons appear **rarely** — generally only in the investment guide on the *Collections* page (one mark per package tier) and on the *Experience* timeline (small connector dots). Icons are never decorative.

- **Style** — thin, mono-line, **1.25–1.5px stroke**, sharp corners, no fills, no rounded caps. Geometric.
- **Color** — champagne gold or charcoal. Never two-tone. Never filled.
- **No emoji.** Anywhere. Ever.
- **No unicode chars as icons** (no `★`, no `✦`, no `❤`).
- **No PNG icons** — all icons are stroke-based vector. The three package-tier marks on Page 3 are inline hairline SVGs drawn at 48×48 with a 1.25px gold stroke.

---

## Logo & marks

A primary wordmark and a monogram glyph live in `assets/`:

- `assets/logo-wordmark.svg` — full lockup, "VERA LUNE" + "STUDIO" with tracked letterspacing and a hairline rule.
- `assets/logo-monogram.svg` — circular `VL` monogram, used at small sizes (favicon, footer, page corners).
- `assets/logo-wordmark-light.svg` — light variant for dark backgrounds.

> These marks are **placeholders constructed from the studio name and the type system.** Drop a real logo file in `assets/` (same filenames) to replace them — every consumer of this system reads from those filenames.

---

## Fonts

The system loads **Cormorant Garamond** and **Montserrat** from Google Fonts at the top of `colors_and_type.css`. Both are open-source web fonts with full Latin coverage and weights that align with the type scale above. See `fonts/README.md`.

---

## Quick start

```html
<link rel="stylesheet" href="colors_and_type.css">
<body class="vl">
  <header>
    <span class="vl-eyebrow vl-eyebrow--gold">The Experience</span>
    <hr class="vl-rule-gold">
    <h1 class="vl-display">A film, slowly told.</h1>
  </header>
  <p class="vl-body">…</p>
</body>
```

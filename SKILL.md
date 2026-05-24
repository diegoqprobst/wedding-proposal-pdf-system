---
name: vera-lune-design
description: Use this skill to generate well-branded interfaces and assets for Vera Lune Studio (a fictional luxury wedding photography & cinema studio), either for production or throwaway prototypes / mocks / client deliverables. Contains essential design guidelines, colors, type, fonts, assets, and the 6-page investment guide PDF template. This is a sanitized, shareable example of a Claude Design system.
user-invocable: true
---

Read the README.md file within this skill, and explore the other available files. Key entry points:

- `colors_and_type.css` — design tokens (palette, type, spacing, motion, semantic element styles).
- `assets/` — wordmark, monogram (type-set placeholders).
- `templates/investment_guide.html` — the 6-page client investment guide. The primary deliverable.
- `templates/CLIENT_DATA_TEMPLATE.txt` — per-client fill-in-the-blanks. Drives PDF regeneration.
- `templates/INSTRUCTIONS.md` — how to personalize and print.
- `HOW_THIS_WAS_BUILT.md` — the Claude Design workflow that produced this system.

If creating visual artifacts (slides, mocks, client guides, throwaway prototypes), copy assets out of this folder and create static HTML files for the user to view. The aesthetic target is **Vogue editorial × fine-art wedding cinema**: full-bleed photography, generous warm-white space, thin champagne-gold rule lines, sharp corners, no gradients, no clipart, no emoji. Cormorant Garamond for headings (italic 300 for the showpiece moments), Montserrat Light for body, eyebrows in 0.32em-tracked uppercase. Em-dashes are the studio's signature punctuation.

If working on production code, copy assets and read the rules in README.md to become an expert in designing with this brand. Pay particular attention to:
- The "Visual foundations — five rules" section.
- The hover / press / focus contract.
- The iconography rules (thin mono-line only; no emoji; no PNG icons).

If the user invokes this skill without any other guidance, ask them what they want to build or design — likely a personalized investment guide, a one-off slide, or a new web page in the studio's voice — ask a few clarifying questions (couple, date, package, hero image), and act as an expert designer who outputs HTML artifacts *or* production code, depending on the need.

# How this system was built in Claude Design

This folder is a **sanitized, shareable example** of a professional design system built in [Claude Design](https://claude.ai/design) and handed off to a coding agent. It documents a repeatable method: turn a one-paragraph brand brief into a reusable, on-brand document-generation system whose primary output is a print-ready client PDF.

Everything here is fictional — "Vera Lune Studio," its clients, contact details, and prices are invented, and all contact values use reserved, non-routable forms (`.example` domain, `555-01xx` phone). Use it as a template for your own work.

---

## The shape of the system

```
colors_and_type.css   →  design tokens: the single source of truth for color, type, spacing, motion
README.md             →  the brand bible: voice, the five visual rules, type/color tables
SKILL.md              →  a portable "skill" manifest so an agent can pick the system up and design in-voice
assets/               →  logo / monogram (type-set placeholders, swappable in place)
templates/            →  the deliverable: a 6-page investment guide + a per-client data system
HOW_THIS_WAS_BUILT.md →  this file
```

Two ideas make it reusable:

1. **Tokens + rules, not one-off styling.** Every color, size, and spacing value lives in `colors_and_type.css` as a `--vl-*` variable, and the README encodes the *judgment* (when to use gold, how much white space, what never to do). A new artifact stays on-brand by consuming tokens and obeying the rules.
2. **Template + data, not copy-paste.** The deliverable is a master template with `data-field="…"` hooks. A plain-text data file per client drives a personalized copy. The design never has to be touched to produce a new client's guide.

---

## The workflow, step by step

### 1 — Write a brand brief
A few lines is enough: palette (hex), type pairing, visual rules, tone, and **what the primary deliverable is**. Naming the deliverable up front ("a client-facing investment guide PDF, generated per client from text data") is what lets the system be built *toward* something instead of in the abstract.

### 2 — Let Claude Design build the foundation first
Before any page is designed, the system lays down: the token CSS, the README brand bible, placeholder logo/marks, and a `SKILL.md` manifest. This foundation is what every later artifact reads from — so a logo or color change propagates everywhere by editing one file.

### 3 — Design the deliverable as a template
The 6-page guide (Cover → Studio → Collections → Experience → Testimonial → Investment) is built once, to letter size, with `@page { margin: 0 }` so it prints exactly as designed. The personalizable spots are marked with `data-field` attributes rather than hard-coded — Page 1 (couple, date, year), Page 3 (selected package + deliverables), Page 6 (package, total, photographer, personal note).

### 4 — Create a plain-text client-data template
`CLIENT_DATA_TEMPLATE.txt` is a fill-in-the-blanks file: one `FIELD_NAME:` per line, comments prefixed with `#`. Non-technical staff can fill it without touching HTML. `templates/INSTRUCTIONS.md` maps each field to where it lands.

### 5 — Generate a personalized copy
Fill the data file for a client, and regenerate `investment_guide_<couple>.html` by substituting each `data-field` and swapping the Page 3 deliverables/price for the chosen package. `investment_guide_amara_and_daniel.html` (from `client_data_amara_and_daniel.txt`) is the worked example.

### 6 — Print to PDF
Open the personalized HTML in Chrome or Safari → *File → Print → Save as PDF*. Because the page is letter-size with zero `@page` margin, the PDF matches the screen exactly.

### 7 — Hand off to a coding agent
Claude Design exports a handoff bundle (README for agents + chat transcripts + the project files). A coding agent reads the transcripts for *intent*, follows the template's imports, and rebuilds the design in whatever the target stack is — recreating the visual output, not necessarily the prototype's structure.

---

## Practices worth copying

- **Ask for source material before inventing.** A real site, past PDFs, or a logo always beat a brand invented from a description. State clearly when something is a placeholder built from the brief alone.
- **Flag every substitution.** Icon library, fonts, and stand-in imagery were *chosen by the system*, not specified — so they're called out as swappable. Make your assumptions visible.
- **Iterate from a real example.** The fastest way to tighten the system is to fill the data template for one real client and refine from there.
- **Keep the rules where they're enforced.** Design judgment lives in the README; values live in the token CSS. Neither duplicates the other.

---

## Adapting this to your own brand

1. Replace the four core colors and the type pairing in `colors_and_type.css`. Rename the `--vl-*` prefix to your own initials if you like (it appears in the CSS and inline in the templates).
2. Rewrite `README.md` voice/rules to your brand, and drop a real logo into `assets/` (same filenames).
3. Keep or reshape the 6-page structure; keep the `data-field` hooks so per-client generation still works.
4. Edit `CLIENT_DATA_TEMPLATE.txt` fields to match what you actually collect.
5. Swap the hairline image placeholders for real photography by setting a background image on the `.photo`, `.left`, and `.thumb` elements.

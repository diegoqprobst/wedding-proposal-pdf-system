# Investment Guide — How to personalize

This folder contains the studio's per-client investment guide system.

| File | Purpose |
|---|---|
| `investment_guide.html` | The 6-page master template. Open in a browser; press `⌘P` / `Ctrl+P` to save as PDF. |
| `investment_guide_amara_and_daniel.html` | A worked example — the master filled for a sample couple. |
| `CLIENT_DATA_TEMPLATE.txt` | Plain-text fill-in-the-blanks for a new client. |
| `client_data_amara_and_daniel.txt` | The filled data file behind the example above. |

## Workflow

1. **Copy `CLIENT_DATA_TEMPLATE.txt`** to a new file named after the couple, e.g. `client_data_rivera.txt`.
2. **Fill in the values** to the right of each `FIELD_NAME:` colon. Keep field names and order unchanged. Lines beginning with `#` are comments.
3. **Regenerate.** A personalized `investment_guide_<couple>.html` is produced by replacing every `data-field="…"` element in the master with the corresponding value, and substituting the Page 3 deliverables for the chosen package.
4. **Print to PDF.** Open the personalized HTML in Chrome or Safari and use *File → Print → Save as PDF*. The page is letter-size with `@page` margin set to zero, so the layout prints exactly as designed.

## Field map

Every field in `CLIENT_DATA_TEMPLATE.txt` corresponds to a `data-field="…"` attribute on Page 1 / 3 / 6 of `investment_guide.html`. The map:

| Template field | Lands on |
|---|---|
| `COUPLE_FIRST_NAME`, `COUPLE_SECOND_NAME` | Page 1 — gold couple line |
| `WEDDING_DATE_LONG` | Page 1 — date sub-line |
| `WEDDING_YEAR_SPELLED` | Page 1 — top of cover |
| `PACKAGE_NAME` | Page 3 — highlighted column · Page 6 — selected collection |
| `INVESTMENT_TOTAL` | Page 6 — gold total |
| `DELIVERABLE_1..6` | Page 3 — list under the chosen package |
| `PHOTOGRAPHER_ASSIGNED` | Page 6 — gold inline mention |
| `PERSONAL_TOUCH_SENTENCE` | Page 6 — replaces the standard "next" paragraph |
| `HERO_IMAGE` | Page 1 — full-bleed background |
| `TESTIMONIAL_*` | Page 5 — pull quote and attribution |
| `STUDIO_*` | Page 6 — contact block |

## Design rules to preserve

When personalizing, **never**:
- Add gradients, glows, or drop shadows.
- Swap the type stack — Cormorant Garamond + Montserrat only.
- Use champagne gold as a fill on text larger than the price/total treatment.
- Introduce additional accent colors.
- Replace em-dashes with hyphens.

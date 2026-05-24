# Fonts

This system uses two open-source typefaces, loaded from Google Fonts via an `@import` at the top of `colors_and_type.css`:

- **Cormorant Garamond** — headings, pull quotes, prices, and the cover display. Italic 300 is the signature showpiece weight.
- **Montserrat** — body, eyebrows, labels, captions, and buttons. Light (300) is the default body weight.

Both have full Latin coverage and the weights the type scale relies on (serif 300/400/500; sans 200/300/400/500).

## Using local font files instead of the CDN

If you'd rather self-host (for offline rendering, print fidelity, or a licensed foundry version):

1. Drop the `.woff2` / `.ttf` files into this `fonts/` folder.
2. Replace the `@import url(...)` line in `colors_and_type.css` with `@font-face` blocks pointing at the local files.
3. Keep the family names in `--vl-serif` and `--vl-sans` aligned, or update those tokens to match.

The fallback chains in `--vl-serif` (`'Garamond', 'EB Garamond', Georgia, serif`) and `--vl-sans` (`'Helvetica Neue', Arial, sans-serif`) are set up to degrade gracefully if a font fails to load.

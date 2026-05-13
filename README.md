# Aylo — Landing Site

A small static site (3 pages + 1 stylesheet). Nothing to build, nothing to compile.
Open `index.html` in a browser and it works. Drop the folder onto any static host
(Vercel, Netlify, Cloudflare Pages, GitHub Pages, S3) and you're live.

## Files

| File          | Purpose |
|---------------|---------|
| `index.html`  | Landing page. Self-contained — all CSS is inline. |
| `privacy.html`| Privacy policy. Pulls styles from `legal.css`. |
| `terms.html`  | Terms of service. Pulls styles from `legal.css`. |
| `legal.css`   | Shared stylesheet for the two legal pages. |

## Stack

- Plain HTML + CSS. No framework, no JS build step.
- Google Fonts: **Quicksand** (wordmark) and **Source Serif 4** (headlines).
- One small SVG of an iPhone with a fake Aylo chat mocked inside it.
- One inline `<svg>` symbol for the gradient heart, reused everywhere.

## Brand specifics — please preserve

- **Wordmark**: Quicksand semibold, **dark ink** (`#23202B`), heart in **coral** (`#E8586E`).
  Never tint the wordmark coral; the heart carries the color.
- **Heart**: linear gradient from `#FF8595` → `#E8586E` → `#C4435D`, top-left to
  bottom-right. Referenced via `<use href="#…"/>` from a hidden `<svg>` defs block.
- **Type pairing**: serif (Source Serif 4, italic for emphasis) for headlines,
  Quicksand for the wordmark, system sans for body.
- **Palette**:
  - Cream paper: `#FAF4E8`
  - Ink: `#23202B`
  - Coral accent: `#E8586E`
  - Soft warm grey: `#E9E4DA`

## Things that still need real input before launch

These are placeholders only. Don't ship without fixing them.

- [ ] **App Store URL** — the "Download on the App Store" button currently points
      at `#`. Replace once the listing is live.
- [ ] **Contact email** — `mailto:hello@aylo.app` in the footer and legal pages.
      Confirm the address exists (or change it).
- [ ] **Legal copy** — `privacy.html` and `terms.html` were drafted in Aylo's
      voice as a starting point, **not** by a lawyer. They MUST be reviewed by
      counsel before launch. Areas that especially need attention:
      data subprocessors (Anthropic, Supabase or whichever backend, RevenueCat,
      Apple), CCPA/GDPR rights language, dispute resolution / governing law.
- [ ] **og:image / favicon** — not included. Add a 1200×630 OG card and a
      coral-heart favicon (16/32/180px).
- [ ] **Apple Sign In branding** — if the App Store listing offers Sign in with
      Apple, the marketing site should mention it (or stay silent — don't claim
      Google only).

## Things to NOT change without checking first

- The hero copy is deliberately dual: half "mirror" (reflection), half "guide"
  (AI help). Both halves matter — earlier drafts that leaned only on the AI
  feature were rejected.
- The three value props (Reflections / Timeline / Patterns) map directly to
  three tabs in the app. Don't rename them on the marketing site without
  renaming them in the app.
- The phone mock is intentionally a chat thread with an uploaded text screenshot
  pinned at the top. That's the headline feature; please don't swap it for a
  generic mood-blob or empty journal.

## Nice-to-haves (if you have time)

- Light analytics (Plausible or similar — avoid GA for privacy fit).
- A short "How it works" section with three numbered steps. Keep it terse.
- Reduced-motion media query around the caret-blink CSS (currently steady).
- Dark-mode pass (cream → deep ink, coral stays coral).

## Deploying

```bash
# Local preview
python3 -m http.server -d web 8000
# → open http://localhost:8000

# Vercel / Netlify
# Drop the `web/` folder into the dashboard, or:
npx vercel deploy --prod web
```

That's it. Have fun.

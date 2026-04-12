# Architecture

## Overview

The Dharma Gate is a **static single-page portal** hosted on GitHub Pages, using the same hub-and-spoke model as TheWayWithin.

- The **hub** (this project) is a landing page with nine scripture cards
- The **spokes** are separate GitHub repositories, each a standalone scripture mini site
- The hub links out to the spokes — it does not embed or import their content

The site uses HTML + CSS only. No frameworks, no build tools.

---

## Hub-and-Spoke Model

```
DharmaGate (hub)
  ├── → HeartSutra (spoke)        github.com/lugh3456/HeartSutra
  ├── → DiamondSutra (spoke)      github.com/lugh3456/DiamondSutra
  ├── → LotusSutra (spoke)        github.com/lugh3456/LotusSutra
  ├── → AvatamsakaSutra (spoke)   github.com/lugh3456/AvatamsakaSutra
  ├── → VimalakirtSutra (spoke)   github.com/lugh3456/VimalakirtSutra
  ├── → AmitabhaSutra (spoke)     github.com/lugh3456/AmitabhaSutra
  ├── → Dhammapada (spoke)        github.com/lugh3456/Dhammapada
  ├── → SuttaNipata (spoke)       github.com/lugh3456/SuttaNipata
  └── → BardoThodol (spoke)       github.com/lugh3456/BardoThodol
```

Each spoke is independently maintained. Adding or activating a spoke only requires updating one card in `index.html` — no other files change.

---

## Folder Structure

```
DharmaGate/
  index.html        ← single portal page (all HTML + CSS in one file)
  manifest.json     ← PWA web app manifest
  sw.js             ← service worker (offline support)
  icons/
    icon-192.png    ← PWA icon (also used as apple-touch-icon)
    icon-512.png    ← PWA icon (splash screen / install prompt)
  docs/
    readme.md       ← project overview
    architecture.md ← this file
    ai-context.md   ← instructions for AI assistants
    plan.md         ← vision and objectives
    roadmap.md      ← phased delivery plan
```

---

## Page Structure

```
<header>              ← site name "The Dharma Gate / 法门" + nav
<section.hero>        ← tagline 戒·定·慧, heading, intro text
<main>
  .divider            ← "THE NINE SCRIPTURES · 九部经典"
  .cards-section      ← CSS Grid, 9 scripture cards
    article.site-card ← one per scripture (coming-soon-badge until live)
<section.about-strip> ← About this collection
<footer>
<script>              ← service worker registration
```

---

## CSS Architecture

All styles are in a `<style>` block inside `index.html`, organised into labelled sections:

```
TOKENS / VARIABLES     ← CSS custom properties (:root)
RESET & BASE
SKIP LINK              ← accessibility
HEADER / NAV
HERO
DIVIDER
SCRIPTURE CARDS        ← .cards-section, .site-card, card children
COMING SOON BADGE
ABOUT STRIP
FOOTER
RESPONSIVE — TABLET    ← ≤ 768px
RESPONSIVE — MOBILE    ← ≤ 600px
RESPONSIVE — SMALL     ← ≤ 360px
SAFE AREA              ← env(safe-area-inset-*) for iPhone notch/home bar
```

---

## Design Tokens

| Token | Value | Usage |
|-------|-------|-------|
| `--red` | `#b83232` | Primary accent (replaces gold from TheWayWithin) |
| `--red-light` | `#d44e4e` | Hover states, logo colour |
| `--saffron` | `#c8820a` | Card category label |
| `--saffron-lt` | `#e09c2a` | Hero tagline, about strip heading |
| `--ink` | `#1c0f0f` | Header, footer backgrounds |
| `--ink-light` | `#2d1a1a` | Hero background |
| `--bg` | `#f7f0e6` | Page background (warm cream) |
| `--surface` | `#ffffff` | Card backgrounds |
| `--text` | `#2d1f1f` | Body text |
| `--muted` | `#7a6060` | Card descriptions, tags |
| `--border` | `#e0d0c8` | Card borders, tag borders |

---

## Card Grid

```css
grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
```

- Desktop (≥ 960px): 3 columns × 3 rows (9 cards fits perfectly)
- Tablet (768px): 2 columns, wraps
- Mobile (≤ 600px): single column

---

## PWA Setup

Three files enable PWA behaviour:

| File | Purpose |
|------|---------|
| `manifest.json` | App name, icons, theme colour, display mode |
| `sw.js` | Caches core assets; serves from cache offline |
| `<meta>` tags in `index.html` | iOS home screen support, status bar colour |

To package as a native app later, wrap in Capacitor (Ionic) or a simple WKWebView shell. The PWA setup ensures all assets are already offline-capable and installable.

---

## Responsive Breakpoints

| Breakpoint | Change |
|-----------|--------|
| > 768px | Default layout, 3-column grid |
| ≤ 768px | Grid min-width shrinks to 260px |
| ≤ 600px | Header stacks; hero padding reduces; cards go single-column |
| ≤ 360px | Logo and heading font sizes reduce |

---

## External Dependencies

Google Fonts (loaded via `<link>`):
- Noto Serif SC — headings, logo, Chinese card names
- Noto Sans SC — body, nav, descriptions

No other external dependencies.

---

## Hosting

GitHub Pages via the `lugh3456` account.
Deployment: push files to repository root on `main` branch.
Planned URL: `https://lugh3456.github.io/DharmaGate/`

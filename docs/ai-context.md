# AI Context — The Dharma Gate

Instructions for AI assistants working on this project.

---

## What this project is

A static Buddhist scripture portal hosted on GitHub Pages. Hub-and-spoke model: one portal page links to nine scripture mini sites (separate GitHub repos). Same architecture as TheWayWithin.

## Current state (as of 2026-04-14)

- Portal hub built: `index.html`, `manifest.json`, `sw.js`, icons
- Logo subtitle: 法门无量 (Fǎmén Wúliàng)
- 9 scripture cards present; Heart Sutra, Diamond Sutra, and Lotus Sutra cards are active; remaining 6 cards marked "COMING SOON"
- Heart Sutra mini site fully built and deployed — https://lugh3456.github.io/HeartSutra/
- Diamond Sutra mini site fully built and deployed — https://lugh3456.github.io/DiamondSutra/ (32 chapters)
- Lotus Sutra mini site fully built — https://lugh3456.github.io/LotusSutra/ (28 chapters)
- Portal deployed to GitHub Pages — https://lugh3456.github.io/DharmaGate/

## Design system

See `architecture.md` for full token list. Key colours:
- Primary accent: red `#b83232` (replaces gold from TheWayWithin)
- Secondary warm: saffron `#c8820a` / `#e09c2a`
- Dark backgrounds: `#1c0f0f` (header/footer), `#2d1a1a` (hero)
- Page background: `#f7f0e6` (warm cream)

Fonts: Noto Serif SC (headings, Chinese), Noto Sans SC (body). Same as TheWayWithin.

## The nine scriptures

| # | English | Chinese | Tradition | Card symbol | Status |
|---|---------|---------|-----------|-------------|--------|
| 1 | Heart Sutra | 般若波罗蜜多心经 | Mahayana | 心 | Active |
| 2 | Diamond Sutra | 金刚般若波罗蜜经 | Mahayana | 金 | Active |
| 3 | Lotus Sutra | 妙法莲华经 | Mahayana | 莲 | Active |
| 4 | Avatamsaka Sutra | 大方广佛华严经 | Mahayana | 华 | Active |
| 5 | Vimalakirti Sutra | 维摩诘所说经 | Mahayana | 维 | Coming soon |
| 6 | Amitabha Sutra | 阿弥陀经 | Mahayana (Pure Land) | 阿 | Coming soon |
| 7 | Dhammapada | 法句经 | Theravada | 法 | Coming soon |
| 8 | Sutta Nipata | 经集 | Theravada | 慈 | Coming soon |
| 9 | Bardo Thodol | 中阴得度 | Vajrayana | 中 | Coming soon |

## How to activate a card (when a mini site is ready)

1. Remove the `<span class="coming-soon-badge">COMING SOON</span>` from the card
2. Add a `<a href="[URL]" class="card-link">Explore [Name] →</a>` button
3. URL format: `https://lugh3456.github.io/[RepoName]/`

## Working rules

- Always back up before editing: create `Backup/YYYY-MM-DD/` and copy all current files
- Follow the same CSS organisation as TheWayWithin (labelled sections)
- Keep all CSS inline in `index.html` — no separate stylesheet
- After any confirmed change, update `roadmap.md` and this file
- Local-first: verify locally before pushing to GitHub

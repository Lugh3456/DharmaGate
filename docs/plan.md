# Plan — The Dharma Gate

## Vision

A clean, bilingual (English + Chinese) portal for personal study of nine of Buddhism's most important scriptures. Each scripture gets its own mini site — consistent in structure but individually designed to suit its content and tradition.

Accessible on desktop, optimised for mobile, and packageable as a native app (iOS/Android) when ready.

## Goals

1. **Study companion** — a go-to reference for reading and reflecting on Buddhist texts
2. **Bilingual** — all content in English and Chinese side by side
3. **Unified but distinct** — all sites share the same design language, but each scripture mini site can have its own character
4. **Mobile-first** — fully usable on phone without compromise
5. **App-ready** — PWA foundation enables packaging as a native app later with minimal extra work

## Scope

### Phase 1 — Portal hub (complete)
- Portal `index.html` with 9 cards, all "coming soon"
- PWA setup (manifest, service worker, icons)
- Docs

### Phase 2 — First scripture mini sites
- Build the first 1–3 scripture mini sites (to be decided)
- Suggested starting point: Heart Sutra (shortest, most popular) and Dhammapada (most accessible for Theravada)
- Activate corresponding cards on the hub

### Phase 3 — Remaining mini sites
- Build remaining scripture sites progressively
- Each site: index page + individual chapter/section pages

### Phase 4 — App packaging
- Wrap PWA in Capacitor or similar for App Store / Google Play submission

## Not in scope (for now)
- User accounts or bookmarking
- Audio recitation
- Search across all sites
- Comments or community features

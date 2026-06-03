# Roadmap

This document tracks planned improvements to Amountomatic, organized by phase.

---

## Phase 1 — Core UX polish

Small, high-value improvements that sharpen the existing prototype.

- **Haptic feedback** — short vibration pulse on token add/remove via the Vibration API (mobile only)
- **Keyboard accessibility** — tab between lanes, space/enter to add a token from the focused lane
- **Undo last token** — single-level undo (`Ctrl+Z` / `Cmd+Z`) removes the most recently added token
- **Configurable currency symbol** — set via a URL parameter (`?currency=€`) or a small config block at the top of the file
- **Persist total across refreshes** — opt-in localStorage persistence so an in-progress tally survives an accidental reload

---

## Phase 2 — Power features

Deeper capabilities for more demanding use cases.

- **Custom denomination editor** — add, remove, or reorder lanes at runtime
- **Subtraction mode** — hold Shift while clicking a drawer token to subtract its value from the total
- **Sound effects** — satisfying click/drop audio with a toggle to disable
- **Structured export** — copy button produces a breakdown like `5×$20 + 2×$100 = $600` in addition to the raw number
- **Dark mode** — respects `prefers-color-scheme` and allows manual toggle

---

## Phase 3 — Platform & integration

Broader reach and composability.

- **Progressive Web App** — service worker for offline use and home-screen installability
- **Embeddable widget** — distribute as a Web Component (`<amount-omatic>`) with a simple script-tag include
- **Multi-currency support** — swap denomination sets for EUR, GBP, JPY, etc., including correct coin/note values
- **URL-shareable state** — encode the current tally in the query string so a session can be shared or bookmarked

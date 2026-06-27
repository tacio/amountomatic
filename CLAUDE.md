# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Amountomatic is a single-file, dependency-free web widget for building up a numeric total by tapping denomination tokens (coins/bills) instead of typing. The **entire application lives in `index.html`** — HTML, CSS (in a `<style>` block), and vanilla JS (in a `<script>` block). There is no framework, no build toolchain, no package manager, and no source tree.

## Running and testing

- **Run:** open `index.html` directly in a browser (`open index.html`) or drag it into a tab. There is no dev server or build step.
- **Tests:** there is no automated test suite. `UX-TEST-PLAN.md` is a manual test matrix (TC-01 … TC-24) covering board init, add/remove tokens, the x100 multiplier, total formatting, sweep, clipboard copy, responsive layout, and edge cases. When changing behavior, find the matching TC entries and verify them by hand; add new TC rows for new behavior.
- **Deploy:** pushing to `main` triggers `.github/workflows/deploy.yml`, which publishes the repo root to GitHub Pages. The site *is* the file — no artifact build happens beyond uploading `.`.

## Architecture and key invariants

The UI is built entirely at runtime by JS; the `<body>` ships with only an empty `#board` and a header. `initBoard()` creates one **lane** per denomination, each containing an `active-area` (the tally stack, `column-reverse` so tokens grow upward) and a `drawer` (holds the single, persistent generator token at the bottom).

Two distinct token types, created by two functions — keep them straight:
- `createDrawerToken(denom)` — the permanent generator in each drawer. Clicking it spawns an active token and adds to the total. It carries `dataset.base` (the unmultiplied value) so its label can be re-rendered when the multiplier toggles.
- `createActiveToken(denom, actualValue, isX100)` — a tally token in the stack. Clicking it subtracts and removes itself. Its value is **baked in** at creation.

**The central invariant: the x100 multiplier is per-token, frozen at the moment of creation.** When a drawer token is clicked, the *current* multiplier is multiplied into `actualValue` and the `x100-marker` visual state is baked into the active token. Toggling x100 afterward only re-labels **drawer** tokens (via `dataset.base`) — it never touches existing active tokens. This is what makes mixed 1× / 100× tallies correct. Do not add logic that retroactively rescales active tokens; TC-10 through TC-12 exist to guard this.

`totalAmount` is the single source of truth, mutated directly on each add/subtract/sweep and rendered by `updateTotal()` with `toLocaleString('en-US')` (commas for display). State is intentionally **not persisted** — refresh resets everything (TC-24). Copy writes the raw integer string (no `$`, no commas) and no-ops when the total is 0.

Denominations are defined once in the `denominations` array; each entry's `class` (e.g. `val-10`) maps to a CSS rule that sets the token's shape, size, and color. The $10 token is rotated 45° with counter-rotation on its inner `<span>` to keep the label upright — any transform changes (active-press scale, x100 text shrink) must compose with that rotation (see the `.val-10` rules).

## Conventions

- Keep it a single self-contained file with zero dependencies — this is a deliberate design constraint, not an accident. Don't introduce a build step, npm, or external libraries without explicit direction.
- New denomination shapes/colors go in the CSS as `.val-N` rules paired with an entry in the `denominations` array.
- `ROADMAP.md` lists planned features (haptics, keyboard a11y, undo, configurable currency, dark mode, PWA, Web Component, etc.) organized by phase — consult it before designing a new feature so the approach fits the intended direction.

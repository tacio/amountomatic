# Amountomatic

A tactile, token-based amount input widget for quickly building up totals.

## What it is

Amountomatic reimagines the numeric input as a physical cash drawer. Instead of typing a number, you tap denomination tokens — coins and bills — that stack up in lanes while a running total updates at the top. It ships as a single, dependency-free HTML file that opens straight in any browser.

## Usage

No build step required. Just open the file:

```
open index.html
```

Or drag it into any browser tab.

## Features

- **7 denominations** — $1 through $100, each with a distinct shape and color
- **x100 multiplier** — toggle to work in hundreds; the multiplier state is frozen into each token at the moment it's added, so mixed-mode tallies stay accurate
- **Stacking token lanes** — tokens pile up with smooth add/remove animations
- **Running total** — locale-formatted display updates in real time
- **Copy to clipboard** — copies the raw integer (no `$`, no commas) for pasting into calculators or forms
- **Sweep** — clears all lanes and resets the total to zero instantly
- **Mobile-responsive** — works on desktop and phone; board scrolls horizontally on narrow screens

## Design notes

- **No persistence by design** — a page refresh starts fresh; there is nothing to sync or corrupt
- **No dependencies** — plain HTML, CSS, and vanilla JS; no build toolchain, no framework
- **Multiplier state is per-token** — switching x100 mode after adding tokens does not retroactively change existing tokens, making mixed tallies predictable

## Contributing & roadmap

See [ROADMAP.md](ROADMAP.md) for planned features and known directions.

# Repository Guidelines

## Project Structure & Module Organization

Amountomatic is a dependency-free, single-page web application. All production code currently lives in `index.html`, including the HTML structure, embedded CSS, and browser JavaScript. The page renders denomination lanes, tracks a running total, supports an x100 multiplier, and copies or clears the result.

Keep small, related changes in `index.html`. If the application grows, extract styles into `assets/css/`, scripts into `assets/js/`, and place automated tests under `tests/`. Do not commit generated files, editor settings, or local server artifacts.

## Build, Test, and Development Commands

No package manager or build step is required. Run a local static server from the repository root:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`. A static server is preferred over opening the file directly because it matches normal browser hosting behavior. There is currently no automated test, lint, or formatting command.

## Coding Style & Naming Conventions

Use two-space indentation for HTML, CSS, and JavaScript. Preserve the existing vanilla JavaScript approach and avoid introducing dependencies without a clear need. Use:

- kebab-case for CSS classes and element IDs (`multiplier-btn`, `total-group`)
- camelCase for JavaScript variables and functions (`totalAmount`, `updateTotal`)
- `const` by default and `let` only for reassigned state

Keep DOM queries near related state declarations, use CSS custom properties for shared colors, and add comments only where behavior is not obvious.

## Testing Guidelines

Manually verify changes in both desktop and narrow mobile viewports. Test every denomination, multiplier toggling, token removal, total formatting, copy behavior, and the Sweep action. Check the browser console for errors. If automated tests are added, name them by user behavior (for example, `multiplier-toggle.test.js`) and document the runner here.

## Commit & Pull Request Guidelines

No accessible commit history establishes a repository-specific convention. Use short, imperative commit subjects such as `Fix token total after multiplier toggle`. Keep each commit focused.

Pull requests should explain the user-visible change, list manual verification performed, and link any relevant issue. Include before-and-after screenshots or a short recording for layout or interaction changes, especially at mobile widths.

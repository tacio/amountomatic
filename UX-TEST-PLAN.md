# UX Test Plan

Manual test plan for the Amountomatic widget prototype.

## Scope & objectives

- Verify all interactive behaviors work correctly across devices and browsers
- Catch edge cases around the multiplier, clipboard copy, and running total accuracy
- Confirm animations and responsive layout render as intended

## Environment matrix

| Platform | Browsers to cover |
|---|---|
| Desktop (≥ 1024 px) | Chrome, Firefox, Safari, Edge |
| Tablet (≈ 768 px) | Chrome (Android), Safari (iOS) |
| Mobile (≤ 390 px) | Chrome (Android), Safari (iOS) |

---

## Test cases

### Board initialization

| ID | Steps | Expected result |
|---|---|---|
| TC-01 | Open `index.html` | 7 lanes render, each with one drawer token labeled with the correct denomination ($1, $2, $5, $10, $20, $50, $100) |
| TC-02 | Observe the total display on load | Shows `$0` |

### Adding tokens

| ID | Steps | Expected result |
|---|---|---|
| TC-03 | Click the drawer token in each lane once | A token appears in the lane's stack; the total increases by the correct denomination amount |
| TC-04 | Click the same drawer token several times | Multiple tokens stack in the lane, overlapping upward; total increments correctly each time |
| TC-05 | Watch the animation when adding a token | Token rises from the drawer and expands into place over ~200 ms |

### Removing tokens

| ID | Steps | Expected result |
|---|---|---|
| TC-06 | Click an active (stacked) token | It scales down and fades out over ~150 ms; total decreases by the token's baked-in value |
| TC-07 | Remove all tokens from a lane | Active area is empty; total remains accurate (no drift from rounding) |

### x100 multiplier

| ID | Steps | Expected result |
|---|---|---|
| TC-08 | Click the **x100** button | Button turns orange; all drawer tokens update their labels to 100× their base value; dotted border appears on drawer tokens |
| TC-09 | Click **x100** again to turn it off | Button returns to grey; drawer token labels revert to base values; dotted border removed |
| TC-10 | Enable x100, add a token, then disable x100 | The added token retains its 100× label and dotted border; total remains correct |
| TC-11 | Add a token in 1× mode, then enable x100 | The existing token keeps its 1× label; no dotted border appears on it |
| TC-12 | Mix 1× and 100× tokens across multiple lanes | Total equals the sum of all individual baked-in values |

### Total display

| ID | Steps | Expected result |
|---|---|---|
| TC-13 | Add tokens until total ≥ $1,000 | Total displays with a comma separator, e.g., `$1,234` |

### Sweep

| ID | Steps | Expected result |
|---|---|---|
| TC-14 | Add several tokens across multiple lanes, then click **Sweep** | All active areas clear instantly; total resets to `$0` |
| TC-15 | Inspect drawer tokens after Sweep | Drawer tokens remain in place and are still functional |

### Copy to clipboard

| ID | Steps | Expected result |
|---|---|---|
| TC-16 | Add tokens to reach a total > 0, click **Copy** | Clipboard contains the raw integer (e.g., `350`, not `$350` or `350.00`) |
| TC-17 | Observe the Copy button after clicking | Button turns green and shows "Copied!" for ~2 seconds, then reverts to its original state |
| TC-18 | Click **Copy** when total is `$0` | Nothing happens — no clipboard write, no visual change on the button |

### Responsive layout

| ID | Steps | Expected result |
|---|---|---|
| TC-19 | View at ≤ 600 px viewport width | Header stacks vertically; buttons stretch to full width within their row |
| TC-20 | View at a very narrow viewport (< 350 px) | Board scrolls horizontally; lanes do not collapse below their minimum width |
| TC-21 | Observe the $10 diamond token at all screen sizes | Token is rotated 45°; label text remains upright (counter-rotation applied) |

### Edge cases

| ID | Steps | Expected result |
|---|---|---|
| TC-22 | Tap a drawer token rapidly many times | Total increments correctly for each tap; no tokens are skipped or doubled |
| TC-23 | Build a very large total (e.g., 100 clicks on $100 in x100 mode = $1,000,000) | Total displays as `$1,000,000`; no overflow or NaN |
| TC-24 | Refresh the page mid-session | Total resets to `$0`; board re-initializes with 7 clean lanes |

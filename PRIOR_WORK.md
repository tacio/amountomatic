# Prior Work on Mobile Numeric-Input Widgets

## Purpose and constraints

Amountomatic studies how people reproduce exact monetary targets. The initial
comparison is a denomination-based token tally against a standard numpad. This
memo surveys other interaction concepts that could become later experimental
conditions.

The shortlist is intentionally constrained to widgets that can run in a mobile
browser:

- portrait-first and touch-first, with desktop support secondary;
- software-only, although physical-interface studies can supply design evidence;
- exact integer-cent input from `$0.01` through `$999.99`;
- no required hover, pressure sensor, hardware dial, voice, or device motion;
- comparable target display, submission control, and usable screen area; and
- observable actions that can be represented in Amountomatic's planned event log.

The main conclusion is to add widgets sequentially, retaining the numpad as a
common anchor. The strongest first candidate is independent digit wheels,
followed by a place-value abacus and a touch-native multiscale scrubber. A radial
pie pad and virtual dial are useful exploratory candidates, but need more
practice or design work before a powered comparison.

## A useful design-space taxonomy

[Oladimeji et al.](https://harold.thimbleby.net/NICE/mobihealth.pdf) divide
number-entry interfaces along two questions: whether users specify digits or
whole numbers, and whether selection is direct or incremental. Their examples
produce four useful families:

| Family | Mechanism | Examples | Characteristic risk |
| --- | --- | --- | --- |
| Serial digit entry | Append digits in sequence | Numpad, handwriting, radial digit strokes | Fast and familiar, but admits missing-digit, transposition, and decimal syntax errors |
| Independent digit entry | Set each place separately | Numeric wheels, up/down digit controls, Comptometer-style columns | Exact and locally editable, but may require moving among many controls |
| Incremental number entry | Move the whole value up or down | Stepper, chevrons, dial | Always stays in range, but can be slow and encourages overshoot/correction |
| Direct number selection | Select a valid value or quantity | Slider, list, tokens, abacus | Makes magnitude visible, but precision and range depend strongly on the representation |

Amountomatic's current conditions already cover serial digit entry (numpad) and
compositional direct selection (token tally). Independent place-value entry and
multiscale incremental entry therefore add the most distinct concepts.

## Evidence matrix

The labels in the **evidence** column distinguish controlled evaluations from
formative studies and concept demonstrations. Results from a different task or
device are design evidence, not predictions of Amountomatic performance.

| Source | Widget or comparison | Context and reported result | Evidence | Mobile fit and limitation |
| --- | --- | --- | --- | --- |
| [Number Entry Interfaces and Their Effects on Error Detection](https://harold.thimbleby.net/cv/files/interact2011.pdf) | Serial keypad versus incremental controls | With 18 participants, serial entry was much faster (mean 1.65 s versus 8.2 s), while incremental entry had fewer undetected errors and far smaller error magnitude | Controlled experiment | Establishes the speed/safety tradeoff, but used a medical-device task rather than mobile currency entry |
| [A Performance Review of Number Entry Interfaces](https://doi.org/10.1007/978-3-642-40483-2_26) | Numpad, chevrons, independent up/down digits, five-key digit editing, and dial | Interface style significantly affected speed and accuracy; the familiar numpad was preferred, while the dial produced many corrected errors | Controlled experiment | Broad comparison and useful error taxonomy, but performed on a physical prototype with hospital-derived values |
| [Assessing the Usability of Six Data Entry Mobile Interfaces for Caregivers](https://humanfactors.jmir.org/2015/2/e15/) | Numeric keyboard, stepper, circle, wheel, columns, and handwriting recognition | Randomized crossover smartphone study with 146 completed participants. Mean time/accuracy were 3.41 s/97.5% for keyboard, 6.02 s/98.2% for stepper, and 6.9 s/97.2% for wheel; circle, columns, and recognition were below 95% accuracy | Controlled mobile experiment | Strongest directly mobile comparison. Ranges were much smaller than 100,000 cent values and participants had only brief practice |
| [Designing Devices With the Task in Mind](https://pubmed.ncbi.nlm.nih.gov/23516794/) | Numpad, chevrons, and five-key digit entry | Real device logs showed that digit and number frequencies were highly nonuniform; the authors argue that interfaces and shortcuts should reflect the actual target distribution | Log analysis plus interface evaluation | Supports stratifying targets by more than magnitude or leading digit; the hospital distribution does not transfer directly to money |
| [Evaluation of Slider Operability in Portable Terminals](https://www.jstage.jst.go.jp/article/his/20/3/20_361/_article/-char/en) | Touchscreen slider target size and control-display ratio | A thumb over 8 mm improved acquisition; movement ratios around 0.7–0.8 improved speed/ease, while 0.3 improved precision | Two controlled mobile experiments | Directly informs touch geometry and suggests an explicit fine-control mode |
| [Investigating the Effect of Orientation and Visual Style on Touchscreen Slider Performance](https://sven-mayer.com/wp-content/uploads/2019/01/colley2018slider.pdf) | Horizontal/vertical and thumb/bar sliders | Twenty participants made 8,080 selections on a 0–100 scale. Only 13.4% were exact; orientation, visual style, and target position produced systematic error | Controlled mobile experiment | Strong evidence against a conventional full-range exact-amount slider; horizontal bar style minimized distortion among the tested designs |
| [Elastic Graphical Interfaces for Precise Data Manipulation](https://www.pitecan.com/papers/CHI95/CHI95.pdf) | FineSlider rubber-band control | Pull distance controls movement speed, allowing coarse travel and fine positioning beyond a conventional slider's pixel resolution | Small controlled evaluation plus concept | The principle transfers to touch, but the original implementation and study were pointer-based |
| [Zliding](https://www.dgp.utoronto.ca/~ravin/papers/uist2005_zliding.pdf) | Concurrent zooming and sliding | Couples value manipulation with a changing control-display ratio for high-precision parameter selection | Controlled stylus experiment | Motivates multiscale control, but pressure must be replaced with an explicit, visible touch gesture |
| [Numeric Input for Industrial Touch User Interfaces](https://publica.fraunhofer.de/entities/publication/24e20851-4249-4ba6-bed9-abd43017f6fa) | Enhanced rotary disc versus two-dimensional point-slider | Both widgets changed value and granularity; the empirical study found the disc concept significantly superior | Controlled touchscreen experiment | Relevant to wide ranges, but details are reported for industrial panels rather than phones |
| [Tweeq](https://doi.org/10.1145/3746059.3747723) | Drag-to-tweak, Ladder UI, sliders, and virtual knobs | Reviews production tools and demonstrates switching among coarse/fine and continuous/discrete control. Ladder UI selects an order of magnitude vertically and adjusts horizontally | Interface review, prototype, informal expert study | A useful modern pattern; Amountomatic must replace mouse buttons and modifier keys with visible touch controls |
| [Knobology Revisited](https://hci.rwth-aachen.de/knobology) | One-touch and two-touch virtual knobs versus tangible controls | Twenty participants were about 20% faster with tangible controls; among virtual knobs, one touch was faster and two touch more accurate | Controlled tabletop experiment | Supplies virtual-knob tradeoffs, but also shows what is lost when no physical control is available |
| [A Comparison of Four Methods of Numeric Entry](https://www.yorku.ca/mack/GI94.html) and [extended pie-pad study](https://www.yorku.ca/mack/GI95.html) | Keypad, handwriting, and clock-direction radial strokes | Keypad initially won on speed, accuracy, and preference. Across 20 later sessions, pie-pad entry became 52% faster and ended 24% faster than handwriting | Controlled experiments, including longitudinal practice | The straight-stroke vocabulary is touch-compatible and learning is relevant to repeated rounds; the studies used a pen and compared digit entry rather than amounts |
| [Assessing Redundant Interface Designs for Precise Number Input in VR](https://web.tecnico.ulisboa.pt/daniel.s.lopes/papers/XR%20NUMPADS%20-%20VRST%202025.pdf) | Conventional numpad, adjustable digit dials, and Comptometer-style columns | Directly editing any decimal place helped simpler edit tasks; conventional entry recovered an advantage on complex tasks. The combined design reduced workload and was preferred | Controlled VR experiment | Supports independent digit editing, but its spatially large VR layouts cannot be copied directly to portrait mobile |
| [Developing a Virtual Abacus Application](https://www.researchgate.net/publication/284012824_Developing_a_System_for_Converting_a_Numeral_Text_into_a_Digit_Number_Abacus_Application) | Direct bead manipulation by place value | Demonstrates a digital abacus in which columns encode ones, tens, hundreds, and higher powers | Concept implementation | Shows feasibility and representation, not competitive entry performance |
| [Feel a Number](https://ir.lib.nycu.edu.tw/handle/11536/48145) and [CoinBeam](https://www.ei-lab.in/projects/coinbeam) | Tangible number and denomination metaphors | Explore how physical quantity and familiar money objects affect the experience of numbers; CoinBeam had an informal study with 11 participants | Design exploration and informal evaluation | Motivates embodied quantity representations, but neither validates a software abacus for fast exact entry |

## Recommended staged widget pipeline

### 1. Independent digit wheels

Build this as the first follow-up condition and compare it against the same numpad
anchor used in the initial study.

The widget should display five independently editable columns as `$ D D D . D D`.
Each column starts at zero and uses vertical touch movement to select a digit from
0 through 9. A tap should focus the column, swiping should move it, and the chosen
digit should visibly settle into a fixed center row. The decimal separator is fixed
and noninteractive, so every reachable state is a valid amount.

Why first:

- it represents the independent-digit family absent from the initial study;
- it covers the complete range exactly without decimal-point syntax;
- smartphone wheel controls already have comparative evidence;
- corrections are local rather than delete-and-retype; and
- five columns fit portrait mobile if touch targets use the full available width.

The study should pay particular attention to column acquisition, accidental
adjacent-column movement, the cost of entering zero-heavy values, and whether
inertial scrolling introduces nondeterminism. The experimental version should not
use free-spinning momentum unless a pilot shows that stopping behavior is stable.

### 2. Place-value abacus

Build a decimal place-value abacus as the second follow-up, not as a cosmetic
variation of the current denomination tally. Use five columns labeled `$100`, `$10`,
`$1`, `10¢`, and `1¢`. Each column encodes one digit from 0 through 9 by moving
beads across a divider; the displayed total updates after every movement.

The representation should have these fixed semantics:

- columns are powers of ten rather than the tally's 1/2/5 denominations;
- each column has exactly ten reachable states, 0–9;
- no automatic carry occurs between columns;
- dragging across the divider and tapping a target bead both set the column count;
- every bead movement emits the affected place, previous digit, next digit, and
  resulting integer-cent value; and
- reset returns every column to zero.

This condition is scientifically interesting precisely because direct performance
evidence is thin. It tests whether visible quantity and place value improve error
detection or learning, at the cost of more visual and motor activity. It should be
piloted for bead occlusion, column width, and whether nine distinct bead positions
remain legible on short screens.

### 3. Multiscale scrubber

Build a touch-native coarse/fine control as the third follow-up. Do not use one
fixed slider spanning 0–99,999 cents; mobile evidence makes exact selection at that
resolution implausible.

Use a horizontal relative scrubber with visible increment bands for `1¢`, `10¢`,
`$1`, `$10`, and `$100`. Touching a band selects the increment; horizontal movement
then adds or subtracts discrete multiples of that increment. The current increment,
direction, and resulting amount must remain visible above the finger. Releasing
commits the current value but does not submit the trial. Users can change bands at
any time and can tap minus/plus affordances as a single-point alternative.

This adapts the Ladder UI and multiscale-slider idea without relying on pressure,
hover, keyboard modifiers, or an invisible vertical-distance rule. Instrument band
changes, drag distance, direction reversals, boundary hits, and overshoots.

### 4. Radial pie pad (exploratory)

The pie pad serially enters digits using straight strokes in clock-face directions;
zero occupies 12 o'clock and digits 1–9 follow clockwise. Use the same implicit-cent
interpretation as the numpad so the only experimental difference is digit-selection
method.

Do not put this into a short first-use comparison. The longitudinal paper found a
large practice effect, so first run a learnability pilot with guided instruction,
recognition feedback, and enough sessions to estimate a learning curve. Record
stroke angle, length, recognized digit, corrections, and preparation time between
strokes.

### 5. Virtual dial (exploratory)

A one-touch virtual dial is preferable to a two-touch version for a general mobile
condition because it is simpler and prior work found it faster, although less
accurate. A viable amount dial still needs an explicit granularity control; one turn
cannot expose 100,000 exact values.

Prototype it only after the scrubber because both investigate multiscale incremental
entry. Reuse the scrubber's visible increment bands, make rotation relative rather
than absolute, support continued turns without a discontinuity at 12 o'clock, and
provide a single-point plus/minus alternative.

## Concepts not recommended as primary conditions

- **Conventional full-range slider:** exact selection is constrained by phone width,
  touch occlusion, and systematic positional error. It is suitable for approximate
  magnitude, not exact cents over the Amountomatic range.
- **Single-rate stepper or chevrons:** these can be accurate but action count grows
  with target magnitude. Multiscale increments are required to make the concept
  viable.
- **Handwriting recognition:** performance depends on a recognition model and
  introduces nondeterministic errors that are not intrinsic to number representation.
- **Voice, tilt, pressure, and camera gestures:** permissions, hardware variation,
  environment, and accessibility would become uncontrolled factors.
- **Physical knobs and tangible coins:** valuable design evidence, but outside a
  software-only open-web experiment.
- **A single session containing every widget:** fatigue, order, and differential
  learning would make interpretation difficult and increase mobile dropout.

## Consequences for the experimental protocol

### Keep a common anchor and stage comparisons

After the initial token-tally versus numpad study, introduce one new widget per
follow-up and retain the numpad as the common anchor. Freeze the anchor's behavior
and version it so results across studies remain interpretable. Do not infer a direct
ranking between new widgets tested in different samples without an appropriate
cross-study model or later head-to-head confirmation.

### Separate first use from learned performance

Novel widgets should have guided practice to a fixed criterion before measured
trials. Still record practice actions and duration. Report first measured performance
and round-over-round learning separately; do not let a composite score hide a widget
that begins slowly but improves rapidly.

The exact practice criterion and measured trial count need a pilot and power analysis.
The pie pad should use a dedicated longitudinal protocol rather than inheriting a
short block designed for familiar controls.

### Expand the raw outcomes

Keep correctness and response time as primary raw outcomes, and add:

- absolute signed error in cents and multiplicative error when defined;
- corrected and uncorrected errors;
- action count and, for continuous gestures, pointer-path length;
- overshoots, direction reversals, and changes of increment/granularity;
- time to first action, time spent correcting, and submission latency;
- abandoned trials and boundary hits; and
- learning rate by widget and round.

This matters because serial entry can be fast while producing rarer but much larger
errors, whereas incremental controls invite visible overshoot and correction.

### Match targets on properties that widgets expose differently

Benford weighting alone is not sufficient for matching blocks once place-value and
incremental widgets are introduced. Record and balance at least:

- amount magnitude and number of significant digits;
- count and location of zero digits;
- repeated digits;
- whether cents are zero, round, or irregular;
- distance from zero and from the nearest round-dollar amount;
- minimum numpad taps;
- minimum digit-wheel changes;
- minimum abacus bead movements;
- minimum scrubber movement at each granularity; and
- minimum token count under the tested denominations.

Widget-specific minimum costs should describe trial difficulty, not be used to make
targets artificially easy for one condition. Difficulty-matched blocks should be
validated after generation and the matching algorithm must be versioned.

### Preserve mobile comparability

All conditions should use the same portrait viewport allocation and the same target,
total, reset, and submit locations. Controls must be usable by touch without browser
zoom, hover, or a hardware keyboard. Test at narrow widths and short viewport heights,
because vertical space is a particular risk for wheels and the abacus.

Gesture widgets must also expose a single-point alternative so the implementation can
meet accessibility requirements. Whether that alternative is permitted in the main
experimental condition must be preregistered and logged rather than silently mixed
with the primary gesture.

## Source-quality notes

- Medical and industrial studies provide unusually detailed error evidence, but their
  safety goals, target ranges, and participant populations differ from open-web money
  entry.
- Slider studies generally evaluate approximate parameter selection over small ranges;
  they justify rejecting an ordinary amount slider more strongly than they validate
  the proposed multiscale scrubber.
- Pie-pad results are old and stylus-based, but their repeated-session design is one of
  the clearest demonstrations that familiarity can reverse an early comparison.
- Abacus and tangible-money work mainly establishes representational ideas. A mobile
  abacus condition would be a new empirical contribution, not a replication of an
  established performance result.
- Recent VR work supports direct editing by decimal place, but the Amountomatic wheel
  must be independently piloted because portrait mobile has far less space and a
  different pointing technique.

## Decision summary

1. Complete and freeze the initial token-tally versus numpad experiment.
2. Pilot and study independent digit wheels against the frozen numpad.
3. Pilot and study a place-value abacus against the same anchor.
4. Pilot and study a visible-band multiscale scrubber.
5. Keep radial pie-pad entry for a learning-focused study and the virtual dial as a
   later multiscale variant.
6. Do not add a conventional slider merely to represent the slider family; it does not
   match the exact, wide-range task.

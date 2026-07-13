# Amountomatic Roadmap

This roadmap evolves the current single-file token tally into a reproducible amount-input experiment. Milestones are ordered: later research depends on stable widget behavior, task generation, and telemetry established earlier.

## 1. Shared Currency and Widget Contract

- Represent all values as integer cents and format them consistently as currency.
- Extract the current embedded styles and scripts only where doing so clarifies widget boundaries.
- Define a widget contract that can initialize and reset, expose its integer-cent value, emit timestamped action/value-change events, and be enabled or disabled during transitions.
- Preserve the current token interactions while adding deterministic unit tests for value changes.

**Exit:** the existing token tally runs through the shared contract with no regression in add, remove, clear, multiplier, or responsive behavior.

## 2. First Two Widgets

- Adapt the token tally to cover cent and dollar denominations without floating-point arithmetic.
- Add an accessible numpad with implicit-cent entry, backspace, clear, and keyboard support.
- Give both widgets the same available space, target display, submission control, and lifecycle.

**Exit:** both widgets can enter every value from `$0.01` to `$999.99`, support mobile and keyboard use where applicable, and pass shared conformance tests.

## 3. Reproducible Trial Generation

- Build a seeded generator with Benford-distributed leading significant digits.
- Stratify targets by magnitude and relevant interaction difficulty, then produce matched but non-identical blocks.
- Store the generator seed, version, and difficulty stratum with every trial.
- Add statistical tests for reproducibility, range limits, leading-digit distribution, and block matching.

**Exit:** a seed deterministically creates a validated 20-trial round with two matched 10-trial blocks.

## 4. Experiment Runner and Telemetry

- Counterbalance widget block order between rounds and participants.
- Start timing at target reveal and end on explicit submission.
- End incorrect trials without revealing correctness; show aggregate results only after both blocks.
- Log participant/session/round/trial IDs, order, target, widget actions with relative timestamps, submission, correctness, elapsed time, device context, and generator metadata.
- Support unlimited rounds and preserve round number for learning-curve analysis.

**Exit:** automated browser tests cover correct and incorrect trials, timing boundaries, counterbalancing, delayed feedback, refresh recovery, and event completeness.

## 5. Local Pilot and Research Freeze

- Export complete sessions as versioned JSON and analysis-ready CSV.
- Run usability and instrumentation pilots across desktop and mobile devices.
- Preregister the Balanced Integration Score formula, standardization population, exclusions, sample-size analysis, learning-curve model, and treatment of abandoned trials.
- Review consent language, data minimization, retention, identity reset, and deletion behavior.

**Exit:** pilot data can reproduce every score from raw events, and the protocol and schema are frozen for the first public study.

## 6. Hosted Study

- Add a small API and database only after the pilot establishes concrete requirements.
- Introduce informed consent, a locally stored pseudonymous participant ID, retry-safe event uploads, and participant-controlled reset/deletion.
- Monitor completion, upload failure, duplicate-event, and dropout rates without collecting directly identifying data.

**Exit:** a staged deployment reliably captures consented sessions, survives intermittent connections, and supports documented data export and deletion procedures.

## 7. Extensible Arena and Analysis

- Publish a widget-registration interface and conformance suite for additional input designs.
- Produce reproducible comparisons of accuracy, response time, Balanced Integration Score, and learning curves.
- Version widgets and protocols so results remain attributable to the exact tested implementation.

**Exit:** a third widget can be added without changing the experiment runner, event schema, or scoring pipeline.

## Later

- Accessibility-focused experimental conditions
- Additional currencies, locales, and amount ranges
- Participant-owned result downloads
- Privacy-reviewed aggregate dashboards
- Reusable study definitions for alternative feedback and assignment protocols

# Amountomatic

Amountomatic is the seed of an arena for studying how people enter monetary amounts. Participants will reproduce randomly generated targets with different input widgets while the application measures correctness, response time, and improvement over repeated rounds.

The current prototype is a dependency-free token-tally widget in [`index.html`](index.html). It offers seven denomination lanes, removable tokens, a ×100 mode, a running total, and copy/clear controls. The experiment runner, numpad, persistence, and analysis described below are planned rather than implemented; see the [roadmap](ROADMAP.md).

Research on mobile numeric-input alternatives—including digit wheels, a place-value abacus, multiscale controls, radial gestures, and dials—is summarized in the [prior-work memo](PRIOR_WORK.md).

## Initial Experiment

The first comparison will use two widgets:

- **Token tally:** an evolution of the current interface with cent and dollar denominations.
- **Standard numpad:** digits enter from the right as implicit cents, as on a payment terminal.

Open-web volunteers may complete as many rounds as they want. Each round contains two counterbalanced blocks of 10 trials—one block per widget—with difficulty-matched but non-identical targets. Timing starts when the target and widget appear and stops on explicit submission. A submission ends the trial whether it is correct or not; correctness is withheld until aggregate results are shown after both blocks.

Targets range from `$0.01` through `$999.99`. Generation will be reproducible from a recorded seed, stratified by magnitude and interaction difficulty, and weighted by Benford's Law for the leading significant digit:

```text
P(d) = log10(1 + 1/d), for d in 1...9
```

This preserves a realistic leading-digit distribution without allowing magnitude or widget-specific difficulty to become an uncontrolled confound.

## Outcomes and Data

The primary comparison will use a preregistered Balanced Integration Score combining accuracy and response time. Raw first-attempt accuracy, response times, completion counts, and round-over-round learning curves will always be reported alongside it. The exact standardization population, response-time treatment, exclusions, and statistical model must be fixed before public collection.

Anonymous event-level telemetry is planned: pseudonymous participant, session, round, and trial IDs; widget and order; target and difficulty stratum; timestamped actions; submitted value; correctness; elapsed time; generator seed/version; and coarse device context. A random participant ID will be stored locally so repeat visits can contribute to learning-curve analysis. Consent must explain this behavior and provide reset and deletion controls. No directly identifying information is required.

## Run the Prototype

No installation or build step is needed. From the repository root, run:

```bash
python3 -m http.server 8000
```

Open <http://localhost:8000>. Test changes at desktop and narrow mobile widths, exercise every denomination and control, and check the browser console for errors.

## Contributing

Start with the [repository guidelines](AGENTS.md) and choose work from the [roadmap](ROADMAP.md). Keep research protocol changes explicit: changes to timing, feedback, target generation, assignment, or telemetry can affect validity and should include a rationale and corresponding tests.

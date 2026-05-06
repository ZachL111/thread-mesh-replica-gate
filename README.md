# thread-mesh-replica-gate

`thread-mesh-replica-gate` packages a practical distributed systems exercise in SQL. The emphasis is on deterministic behavior, a small public API, and examples that explain the tradeoffs.

## How I Read Thread Mesh Replica Gate

The useful thing to inspect here is how the same score rule is represented in code, metadata, and examples. If those three pieces disagree, the audit script should make the drift visible.

## Internal Model

The core is a scoring model over demand, capacity, latency, risk, and weight. That keeps node state, quorum behavior, and lease timing in one explicit decision path. The threshold is 150, with risk penalty 5, latency penalty 2, and weight bonus 5. The SQL project uses sqlite fixtures, views, and assertions to keep query behavior inspectable.

## Problem Shape

This project keeps the domain idea close to the tests. That makes it useful as a reference implementation, a small experiment, or a starting point for a more specialized tool.

## Main Behaviors

- Uses fixture data to keep quorum behavior changes visible in code review.
- Includes extended examples for lease timing, including `recovery` and `degraded`.
- Documents message ordering tradeoffs in `docs/operations.md`.
- Runs locally with a single verification command and no external credentials.
- Stores project constants and verification metadata in `metadata/project.json`.

## Scenario Walkthrough

The examples are meant to be readable before they are exhaustive. They cover enough variation to show how latency and risk can pull a decision below the threshold.

## Repository Map

- `tests`: verification harness
- `fixtures`: compact golden scenarios
- `examples`: expanded scenario set
- `metadata`: project constants and verification metadata
- `docs`: operations and extension notes
- `scripts`: local verification and audit commands
- `schema.sql`: sqlite schema and view definitions

## Run It Locally

The only required setup is the local SQL toolchain. After cloning, stay in the repo root so fixture paths resolve correctly.

## How To Run It

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

This runs the language-level build or test path against the compact fixture set.

## Validation

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/audit.ps1
```

The audit command checks repository structure and README constraints before it delegates to the verifier.

## Known Edges

The examples cover useful edges, not every edge. A larger version would add malformed-input tests, richer reports, and deeper domain parsers.

## Follow-Up Work

- Split the scoring constants into a typed configuration object and validate it before use.
- Add a comparison mode that shows how decisions change when one signal is adjusted.
- Add a loader for `examples/extended_cases.csv` and promote selected cases into the language test suite.
- Add one more distributed systems fixture that focuses on a malformed or borderline input.

# thread-mesh-replica-gate

`thread-mesh-replica-gate` explores distributed systems with a small SQL codebase and local fixtures. The technical goal is to implement an SQL distributed systems project for replica stream reduction, using windowed input fixtures and late-data behavior checks.

## Why This Exists

The point is to make a small domain rule concrete enough that a reader can change it and immediately see what broke.

## Thread Mesh Replica Gate Review Notes

For a quick review, compare `quorum health` with `lease drift` before reading the middle cases.

## Capabilities

- `fixtures/domain_review.csv` adds cases for quorum health and lease drift.
- `metadata/domain-review.json` records the same cases in structured form.
- `config/review-profile.json` captures the read order and the two review questions.
- `examples/thread-mesh-replica-walkthrough.md` walks through the case spread.
- The SQL code includes a review path for `quorum health` and `lease drift`.
- `docs/field-notes.md` explains the strongest and weakest cases.

## Implementation Shape

The implementation keeps the scoring rule plain: reward signal and confidence, preserve slack, penalize drag, then classify the result into a review lane.

The SQL checks add a separate view over the domain review fixture.

## Local Usage

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

## Verification

The check exercises the source code and the review fixture. `baseline` is the high score at 206; `stress` is the low score at 151.

## Roadmap

This remains a local project with deterministic fixtures. It does not depend on credentials, hosted services, or live data. Future work should add richer malformed inputs before widening the public API.

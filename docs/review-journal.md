# Review Journal

The cases below are the review handles I would use before changing the implementation.

The local checks classify each case as `ship`, `watch`, or `hold`. That gives the project a small review vocabulary that matches its distributed systems focus without claiming live deployment or external usage.

## Cases

- `baseline`: `quorum health`, score 206, lane `ship`
- `stress`: `lease drift`, score 151, lane `ship`
- `edge`: `replica lag`, score 172, lane `ship`
- `recovery`: `membership churn`, score 189, lane `ship`
- `stale`: `quorum health`, score 188, lane `ship`

## Note

This file is intentionally plain so the fixture remains the source of truth.

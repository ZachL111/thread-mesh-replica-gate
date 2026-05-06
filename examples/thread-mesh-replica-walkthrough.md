# Thread Mesh Replica Gate Walkthrough

This walk-through keeps the domain vocabulary close to the data instead of burying it in prose.

| Case | Focus | Score | Lane |
| --- | --- | ---: | --- |
| baseline | quorum health | 206 | ship |
| stress | lease drift | 151 | ship |
| edge | replica lag | 172 | ship |
| recovery | membership churn | 189 | ship |
| stale | quorum health | 188 | ship |

Start with `baseline` and `stress`. They create the widest contrast in this repository's fixture set, which makes them better review anchors than the middle cases.

The useful comparison is `quorum health` against `lease drift`, not the raw score alone.

# Field Notes

`thread-mesh-replica-gate` is easiest to review by starting with the fixture, not the prose.

The domain cases cover `quorum health`, `lease drift`, `replica lag`, and `membership churn`. They sit beside the smaller starter fixture so the project has both a compact scoring check and a domain-flavored review check.

The widest spread is between `quorum health` and `lease drift`, so those are the first two cases I would preserve during a refactor.

The language-specific addition keeps the review model as queryable sqlite views and assertions.

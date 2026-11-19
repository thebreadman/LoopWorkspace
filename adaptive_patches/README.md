# Adaptive Loop patches (next-dev)

`patches/adaptive_shadow_nextdev_v2.patch` is applied automatically by "4. Build Loop" (its Customize Loop
step applies everything in `patches/`). It is written for this branch's Loop (next-dev, Loop commit
6990c67). It adds a research shadow: after each loop cycle it logs what the stacking rule would have let
through of the automatic insulin Loop just chose (half of it for 2 h after a hand bolus of 1 U or more,
none within 30 min of a reading under 70).

**It never changes a dose.** It runs after the cycle has finished and dosed, in a separate task, and
nothing it computes is read by Loop.

- Log: Loop's Documents folder, `AdaptiveShadow/stacking_shadow.jsonl`, one JSON line per loop.
- The last 28 days appear at the end of Loop's Issue Report, under "## AdaptiveShadow".
- To remove it: delete `patches/adaptive_shadow_nextdev_v2.patch` and build again.
- next-dev changes often. If an update changes the lines this patch touches, the build stops at
  Customize Loop (nothing is installed); the patch then needs refreshing.

# Adaptive Loop patches

`patches/adaptive_shadow_v1.patch` is applied automatically by "4. Build Loop" (its Customize Loop step
applies everything in `patches/`). It adds a research shadow to Loop: after each loop it logs what the
stacking rule would have let through of the automatic insulin Loop just gave (half of it for 2 h after a
hand bolus of 1 U or more, none within 30 min of a reading under 70).

**It never changes a dose.** It runs after Loop has enacted its dose, on its own low-priority queue, and
nothing it computes is read by Loop.

- Log: Loop's Documents folder, `AdaptiveShadow/stacking_shadow.jsonl`, one JSON line per loop.
- The last 7 days appear in Loop > Settings > Support > Share Diagnostic Report, under "## AdaptiveShadow".
- To remove it: delete `patches/adaptive_shadow_v1.patch` and build again.
- If a future Loop update changes the lines this patch touches, the build stops at Customize Loop
  (nothing is installed); the patch then needs refreshing.

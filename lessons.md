# Lessons learned

Add one line per real test or insight: date — set — what happened — lesson.

- 2026-11-15 — general — Long "do everything at once" prompts tend to produce truncated or buggy output; split big build steps.
- 2026-11-15 — general — Reading dimensions from an image is error-prone; always add a "wait for my confirmation" checkpoint before building.
- 2026-11-15 — 3d-city-district-flyover — Pattern worth reusing everywhere: one object type per message, "keep everything already built exactly as it is", then "tell me which part looks least real".
- 2026-11-16 — floor-plan-walkthrough-harsh-critic — Strongest patterns: (1) read-back table + check against plan totals + "ask, don't guess"; (2) a fresh chat as critic with a score threshold ("a 7 isn't done").

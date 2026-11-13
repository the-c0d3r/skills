---
name: debugging
description: Use during active debugging sessions — diagnosing bugs, tracing failures, investigating why something doesn't work as expected.
---

- Never silence errors while debugging (no `2>/dev/null` or equivalent) until the script is confirmed working.
- When a manual command works but a scripted version doesn't, print the exact command the script is constructing as the first debugging step.
- Work outward from the simplest explanation; trace data flow; know the tool's ceiling. The fix is usually boring — resist elaborate theories before ruling out the obvious.
- One variable at a time — each change should test one specific hypothesis. Changing multiple things at once and succeeding means you don't know what actually worked.
- Dead-end recognition — if two or three variations of the same approach haven't made progress, the approach is probably wrong. Step back and question the assumption that led there.
- Diagnosis should be driven by actual data (logs, meters, counters, profiling output) before proposing a fix.
- Distinguish symptom from root cause explicitly — misleading readings (idle vs. under-load) are a known failure mode.
- Treat "hard requirements" as provisional until tested — flag it when a stated requirement looks like an anchor rather than a real need.
- Before asking the user to test something end-to-end (e.g. in a browser), verify the fix works in a debug script first.
- When validating a fix, test both the failing cases and a control group of currently-working cases through the same change. Ship only if failures improve AND controls don't regress — fixes for A can silently break B.
- Diagnostic tools must reproduce the exact conditions of the production code path they stand in for. Different auth, UA, or network path produces false signal in both directions.
- When implementing an approved visual design, take screenshots and compare against the mockup before reporting done — verifying that an element exists or a toggle works is not visual verification. When using CSS custom properties (`var(--x)`), confirm each token is defined in the target stylesheet; a missing token fails silently with no error.

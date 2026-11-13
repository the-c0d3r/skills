---
name: e2e-tests
description: Use when writing, adding, or creating end-to-end or integration tests.
---

Write end-to-end tests for the current project. Apply every principle below when designing and implementing the tests.

## Principles

### Check all exit codes
Every subprocess, helper, and teardown step must have its exit code checked. When a harness runs a subject and a separate validator, both must pass — a green validator does not excuse a crashed subject. Tests that intentionally expect failure need an explicit way to express the expected exit code (annotation, config file, etc.); default to expecting 0.

### Surface teardown failures
Cleanup failures must be reported (as warnings at minimum), not swallowed. Silent teardown failures leave stale state that corrupts subsequent runs.

### Make tests portable
Avoid OS-specific commands or flags. Prefer the language runtime already in use (e.g. Python, Node) for operations like file sizing or date formatting rather than shell tools that behave differently across platforms.

### Make tests deterministic
Remove all sources of non-determinism: set explicit timestamps when ordering matters, seed random number generators, avoid depending on filesystem or network timing. If a test can fail for a reason unrelated to the code under test, eliminate that reason.

### Validate identity, not just aggregates
Assert *which specific* items were produced, changed, or deleted — not just a count. A count check passes even when the wrong items remain.

### Validate content, not just presence
For structured outputs (files, API responses, DB rows), assert field values — not just that the output exists or has the right number of lines.

### Cover all branches
Every feature flag, policy, config option, and code path needs at least one test. Untested branches are silently broken by definition.

### Test error and warning paths
Each error condition needs a test that verifies both the exit code and the message. Warning-only paths (successful exit + diagnostic output) are distinct from error paths and need their own tests.

### Test boundary conditions
Add a test at the exact limit to confirm the boundary is handled correctly (e.g. at-capacity is not over-capacity). Make the comparison operator (`>` vs `>=`) explicit in the test name or comment.

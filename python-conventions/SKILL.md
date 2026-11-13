---
name: python-conventions
description: Use when writing, editing, or reviewing Python (.py) files or Python scripts.
---

Target Python 3.8, never the newest release: recent versions are missing
on many systems. Never take the interpreter version a tool picks by
default (e.g. `uv init` uses the newest installed).
- Projects: `requires-python = ">=3.8"`, a `.python-version` of `3.8`,
  and dependency versions that still support 3.8 (pin an older release
  if the latest dropped it).
- Code: no syntax or stdlib newer than 3.8 — no `match`, `X | Y` or
  `list[str]` annotations at runtime, parenthesised `with` groups,
  `str.removeprefix`, `zoneinfo`, `tomllib`, `ExceptionGroup`.
- Test on a 3.8 interpreter (`uv python install 3.8`) before calling it done.

Use the `logging` module instead of `print()` for operational output in
any Python program. Set up a module-level `logger = logging.getLogger(...)`
with appropriate handlers and levels. Reserve `print()` only for CLIs
where stdout output is the explicit product (e.g. a query tool printing
results).

For scripts that run unattended, use this handler setup:
- `TimedRotatingFileHandler` — daily rotation, 30-day retention
- stderr handler for WARNING+
- optional stdout handler for INFO when `--verbose` / `--dry-run` is active

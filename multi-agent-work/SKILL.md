---
name: multi-agent-work
description: Use when spawning parallel/sub-agents, coordinating multiple agents writing to shared resources (ID counters, manifests, indices, address files), or when an agent ingests external content via URL/file fetch.
---

- When spawning parallel agents that write to shared resources, audit for
  collisions after every round — parallel agents will overwrite each
  other without knowing.
- After agents ingest external content (URLs, files), verify the output
  contains real content. Fetch tools can fail silently, and the agent may
  generate plausible-looking fabrications instead of flagging the
  failure.
- If a project has scripts for maintaining managed files (indices, logs,
  counters, manifests), always use them instead of directly editing those
  files. Scripts enforce invariants (atomic allocation, trimming,
  date-bumping) that manual edits bypass.

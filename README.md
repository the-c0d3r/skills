# skills

Personal [Claude Code skills](https://docs.claude.com/en/docs/claude-code/skills). Each directory is one skill: a `SKILL.md` with frontmatter (`name`, `description`) and instructions Claude loads when the description matches the task.

## Skills

| Skill | Use when |
|---|---|
| [client-docs](client-docs/SKILL.md) | Writing or reviewing client-facing documents (threat models, design docs, reports) |
| [debugging](debugging/SKILL.md) | Diagnosing bugs and tracing failures |
| [discussion-protocol](discussion-protocol/SKILL.md) | Critiquing an idea, argument, plan or conclusion |
| [e2e-tests](e2e-tests/SKILL.md) | Writing end-to-end or integration tests |
| [multi-agent-work](multi-agent-work/SKILL.md) | Running parallel sub-agents, shared-resource writes, or ingesting external content |
| [nix-conventions](nix-conventions/SKILL.md) | Writing `.nix` files or NixOS configuration |
| [presentations](presentations/SKILL.md) | Writing or reviewing slide decks |
| [product-planning](product-planning/SKILL.md) | Creating, reviewing or cleaning up a product plan |
| [project-retrospective](project-retrospective/SKILL.md) | Starting or reviewing a project retrospective |
| [python-conventions](python-conventions/SKILL.md) | Writing or reviewing Python (targets 3.8) |


## Install

Copy or symlink a skill directory into `~/.claude/skills/` (all projects) or `<project>/.claude/skills/` (one project):

```sh
git clone git@github.com:the-c0d3r/skills.git
ln -s "$PWD/skills/debugging" ~/.claude/skills/debugging
```

Claude Code picks up new skills on the next session. Invoke one explicitly with `/<skill-name>`, or let Claude load it when the task matches its description.

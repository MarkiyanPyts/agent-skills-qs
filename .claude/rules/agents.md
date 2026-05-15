# Subagent authoring rules

- Subagent files live at `.claude/agents/<name>.md`. Frontmatter must include `name`, `description`, and `model`. Use `skills:` to attach skills by name.
- The `description` field drives delegation — write it as a trigger condition ("Use this agent when..."), not as a capability list.
- Prefer `haiku` for narrow, mechanical agents (e.g. `dice-gambler`); reserve larger models for agents that need to reason across files.
- If an agent needs persistent state, set `memory: project` and write to `.claude/agent-memory/<agent-name>/`. Do not write subagent state into the top-level user memory.

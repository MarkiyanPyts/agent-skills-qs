# Skill authoring rules

- Every `SKILL.md` must start with frontmatter containing `name` and `description`. The description is the only field used during discovery — make it specific enough that the agent can decide relevance without reading the body.
- Keep skill bodies short and imperative. They are injected verbatim once activated; long prose wastes context.
- The `roll-dice` skill exists in both `.claude/skills/roll-dice/` and `.agents/skills/roll-dice/`. Edits to one must be mirrored to the other.
- Skill `name` in frontmatter must match the directory name.

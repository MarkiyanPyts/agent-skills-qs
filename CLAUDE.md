# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This repo is a quickstart/demo for Claude Code's **Agent Skills** feature. It contains no application code — only skill and agent definition files used to demonstrate progressive disclosure of skills.

## Architecture

The repo wires together two concepts that work in tandem:

- **Skills** (`.claude/skills/<name>/SKILL.md`, also `.agents/skills/<name>/SKILL.md`) — Markdown files with YAML frontmatter (`name`, `description`) followed by instructions. Discovery is by description only; the body loads into context only when the description matches the user's request. This is the "progressive disclosure" pattern described in [README.md](README.md).
- **Subagents** (`.claude/agents/<name>.md`) — Frontmatter declares `name`, `description`, `model`, `memory` (e.g. `project`), and a `skills:` list pointing at skill names. The body is the agent's system prompt. The `dice-gambler` agent at [.claude/agents/dice-gambler.md](.claude/agents/dice-gambler.md) shows the full pattern: it pulls in the `roll-dice` skill on demand.
- **Agent-scoped memory** lives under `.claude/agent-memory/<agent-name>/` (see [.claude/agent-memory/dice-gambler/roll_log.md](.claude/agent-memory/dice-gambler/roll_log.md)). This is distinct from the top-level user memory at `~/.claude/.../memory/` — these files persist state for a specific subagent across conversations.

Note the duplication between [.claude/skills/roll-dice/SKILL.md](.claude/skills/roll-dice/SKILL.md) and [.agents/skills/roll-dice/SKILL.md](.agents/skills/roll-dice/SKILL.md): `.claude/skills/` is the standard discovery location for skills available to the main agent, while `.agents/skills/` is a separate location keyed off the `.agents/` directory. Keep both in sync if editing the dice skill.

## Conventions

- SKILL.md files must begin with frontmatter containing `name` and `description`. The description is the only thing the discovery pass sees — write it so the agent can decide relevance without reading the body.
- Keep skill bodies short and action-oriented; they get loaded verbatim into the working context once activated.
- When adding a new skill, decide whether it should be available to the main agent (`.claude/skills/`), to a specific subagent (reference it from that agent's `skills:` frontmatter), or both.

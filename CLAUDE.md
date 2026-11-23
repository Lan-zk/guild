# CLAUDE.md

Guild is a collection of Agent Skills for Claude Code and other coding agents, distributed as a Claude Code plugin and via the `skills` CLI.

All repository rules live in AGENTS.md:

@AGENTS.md

## Claude Code specifics

- Plugin skills are auto-discovered from `skills/` — no manifest entry is needed when adding a skill.
- To test the plugin locally, run `/plugin marketplace add ./` in this directory, then install `guild@guild`.
- Skills load on demand by their `description`; keep descriptions specific.

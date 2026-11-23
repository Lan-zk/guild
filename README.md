<p align="center">
  <img src="docs/logo/logo.svg" alt="Guild logo" width="160">
</p>

# Guild

[![Agent Skills](https://img.shields.io/badge/format-Agent%20Skills-blueviolet)](https://agentskills.io)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-plugin-d97757)](https://docs.claude.com/en/docs/claude-code)
[![npx skills](https://img.shields.io/badge/npx-skills-black)](https://skills.sh)

**English** · [简体中文](README-zh.md)

A growing guild of [Agent Skills](https://agentskills.io) — reusable capabilities that teach coding agents how to perform specialized tasks in a repeatable way.

Skills in this repository target [Claude Code](https://docs.claude.com/en/docs/claude-code) first and follow the portable `SKILL.md` format, so they also work with other coding agents that read that format — Codex, Pi, [DSH (DeepSeek Harness)](https://github.com/deepseek-ai/deepseek-harness), Cursor, Gemini CLI, OpenCode, and more.

## How skills work

Each skill is a self-contained folder holding a `SKILL.md` file: YAML frontmatter with `name` and `description`, followed by instructions, scripts, and reference material. Agents read only the frontmatter up front, and load the full skill when a task matches its description.

## Install

### Claude Code (plugin marketplace)

```
/plugin marketplace add Lan-zk/guild
/plugin install guild@guild
```

All skills arrive as a single plugin and update together. You can also browse with `/plugin` → `Browse and install plugins` → `guild`.

### Any agent (skills CLI)

```bash
# Pick skills and target agents interactively
npx skills add Lan-zk/guild

# Or install one skill into specific agents
npx skills add Lan-zk/guild --skill <skill-name> -a codex -a pi
```

### Manual

Copy a skill folder into the directory your agent reads. Most agents share the `.agents/skills/` convention, either per project or per user:

| Agent | Project | User |
| ----- | ------- | ---- |
| Claude Code | `.claude/skills/` | `~/.claude/skills/` |
| Codex | `.agents/skills/` | `~/.agents/skills/` |
| Pi | `.agents/skills/` | `~/.agents/skills/` |
| DSH (DeepSeek Harness) | `.dsh/skills/`, `.agents/skills/` | `~/.dsh/skills/`, `~/.agents/skills/` |
| Cursor | `.agents/skills/` | `~/.cursor/skills/` |
| Gemini CLI | `.agents/skills/` | `~/.gemini/skills/` |
| OpenCode | `.agents/skills/` | `~/.config/opencode/skills/` |
| GitHub Copilot | `.agents/skills/` | `~/.copilot/skills/` |

```bash
# Shared convention (Codex, Pi, DSH, Cursor, Gemini CLI, OpenCode, ...)
cp -r skills/<skill-name> .agents/skills/      # this project
cp -r skills/<skill-name> ~/.agents/skills/    # all projects

# Claude Code
cp -r skills/<skill-name> .claude/skills/
cp -r skills/<skill-name> ~/.claude/skills/
```

> DSH scans only one level deep (`<root>/<name>/SKILL.md`) and prefers `.dsh/skills/` over `.agents/skills/` when both exist.

## Available skills

Skills live in [`skills/`](skills).

| Skill | Description |
| ----- | ----------- |
| [get-me](skills/get-me/SKILL.md) | Confirms the agent genuinely understands your intent before acting — restates it in plain, concrete language, surfaces ambiguity, and waits for your confirmation. |

## Repository layout

```
guild/
├── .claude-plugin/
│   ├── marketplace.json   # Claude Code plugin marketplace manifest
│   └── plugin.json        # Plugin metadata
├── skills/                # One directory per skill
│   └── <skill-name>/
│       ├── SKILL.md       # Required: frontmatter + instructions
│       ├── scripts/       # Optional: executable helpers
│       ├── references/    # Optional: docs loaded on demand
│       └── assets/        # Optional: templates and media
├── docs/
│   └── logo/              # Logo artwork (PNG and SVG)
├── AGENTS.md              # Rules for AI agents working in this repository
├── CLAUDE.md              # Claude Code entry point
├── LICENSE                # Apache License 2.0
├── NOTICE                 # Copyright attribution
├── README.md              # This file
└── README-zh.md           # Chinese translation
```

## Adding a skill

1. Create `skills/<kebab-case-name>/SKILL.md`:

   ```markdown
   ---
   name: <kebab-case-name>
   description: What it does and when to use it, in one or two sentences.
   ---

   Instructions the agent follows. Reference bundled files by relative path.
   ```

2. Name the directory and the frontmatter `name` identically, in kebab-case.
3. Keep the skill self-contained; put large reference material under `references/` so it is loaded only when needed.
4. Add a row to the skills table in **both** `README.md` and `README-zh.md` (see [`AGENTS.md`](AGENTS.md)).

## Contributing

Keep `README.md` and `README-zh.md` content-equivalent. If you work with an AI agent, [`AGENTS.md`](AGENTS.md) makes it update the docs for you.

## License

Licensed under the [Apache License 2.0](LICENSE). Copyright 2026 Lan-zk.

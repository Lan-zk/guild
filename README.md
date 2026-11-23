# Guild

[![Agent Skills](https://img.shields.io/badge/format-Agent%20Skills-blueviolet)](https://agentskills.io)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-plugin-d97757)](https://docs.claude.com/en/docs/claude-code)
[![npx skills](https://img.shields.io/badge/npx-skills-black)](https://skills.sh)

**English** · [简体中文](README-zh.md)

A growing guild of [Agent Skills](https://agentskills.io) — reusable capabilities that teach coding agents how to perform specialized tasks in a repeatable way.

Skills in this repository target [Claude Code](https://docs.claude.com/en/docs/claude-code) first and follow the portable `SKILL.md` format, so they also work with any agent supported by the [skills CLI](https://github.com/vercel-labs/skills) (Codex, Cursor, OpenCode, and more).

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

# Or install one skill into one agent
npx skills add Lan-zk/guild --skill <skill-name> -a claude-code
```

### Manual

```bash
# Personal skills (all projects)
cp -r skills/<skill-name> ~/.claude/skills/

# Project skills (this project only)
cp -r skills/<skill-name> .claude/skills/
```

## Available skills

No skills yet — the collection is being seeded. New skills are listed here and live in [`skills/`](skills).

| Skill | Description |
| ----- | ----------- |

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
├── AGENTS.md              # Rules for AI agents working in this repository
├── CLAUDE.md              # Claude Code entry point
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

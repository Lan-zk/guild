# AGENTS.md

Guidance for AI agents working in this repository. Claude Code loads this file through [`CLAUDE.md`](CLAUDE.md).

## What this repository is

**Guild** is a growing collection of [Agent Skills](https://agentskills.io) for Claude Code and other coding agents. Every skill is a self-contained folder under `skills/` following the portable `SKILL.md` format. The repository is also a Claude Code plugin marketplace, so the whole collection can be installed as one plugin.

```
.claude-plugin/marketplace.json   # marketplace manifest; plugin "guild" points at the repo root
.claude-plugin/plugin.json        # plugin metadata
skills/<skill-name>/SKILL.md      # auto-discovered by the plugin and by `npx skills`
skills/<skill-name>/scripts/      # optional executables
skills/<skill-name>/references/   # optional docs loaded on demand
skills/<skill-name>/assets/       # optional templates and media
```

## Skill conventions

- One directory per skill: `skills/<kebab-case-name>/`.
- `SKILL.md` is required, with YAML frontmatter:

  ```markdown
  ---
  name: <kebab-case-name>
  description: What it does and when to use it, in one or two sentences.
  ---
  ```

- `name` must match the directory name and be unique in the repository.
- The `description` is how agents decide to load the skill; make it specific about trigger conditions.
- Skills must be self-contained: reference bundled files by paths relative to the skill directory. Large reference material goes in `references/`, not inline in `SKILL.md`.
- Never rely on absolute paths, secrets, or environment state that is not documented in the skill.

## Distribution

- The plugin's skills are auto-discovered from `skills/`; there is no explicit skill list to maintain.
- Keep the install paths stable: moving a skill directory breaks `npx skills` installs and the README links.
- On behavior-changing releases, bump `version` (semver) in both `.claude-plugin/marketplace.json` and `.claude-plugin/plugin.json`.

## Documentation sync (mandatory)

Whenever you change this repository — add, rename, remove, or update a skill; change the layout; change install or distribution behavior — update **both** `README.md` and `README-zh.md` **in the same commit**, keeping them content-equivalent:

1. Update the skills table in each file with the skill's name, a link to its `SKILL.md`, and a one-line description.
2. Update install commands, the repository layout tree, and any other affected section.
3. The English file is the source; translate changes into `README-zh.md` in the same change.

A commit that changes behavior without matching README updates in both languages is incomplete.

## Git

- Do not run `git commit` or `git push` unless the user explicitly asks for it.
- Group related changes into a single commit; do not split one logical change across commits.

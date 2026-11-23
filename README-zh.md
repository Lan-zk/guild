<p align="center">
  <img src="docs/logo/logo.svg" alt="Guild 徽标" width="160">
</p>

# Guild

[![Agent Skills](https://img.shields.io/badge/format-Agent%20Skills-blueviolet)](https://agentskills.io)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-plugin-d97757)](https://docs.claude.com/en/docs/claude-code)
[![npx skills](https://img.shields.io/badge/npx-skills-black)](https://skills.sh)

[English](README.md) · **简体中文**

Guild 是一个持续生长的 [Agent Skills](https://agentskills.io) 技能库 —— 把可复用的能力沉淀成技能，让编码智能体以可重复的方式完成专业化任务。

本仓库的技能优先面向 [Claude Code](https://docs.claude.com/en/docs/claude-code)，并遵循可移植的 `SKILL.md` 格式，因此也能用于其他读取该格式的编码智能体 —— Codex、Pi、[DSH（DeepSeek Harness）](https://github.com/deepseek-ai/deepseek-harness)、Cursor、Gemini CLI、OpenCode 等。

## 技能如何工作

每个技能是一个自包含的目录，内含 `SKILL.md`：YAML frontmatter 提供 `name` 和 `description`，其后是使用说明、脚本和参考资料。智能体启动时只读取 frontmatter，在任务与描述匹配时才加载完整技能内容。

## 安装

### Claude Code（插件市场）

```
/plugin marketplace add Lan-zk/guild
/plugin install guild@guild
```

所有技能作为一个插件整体安装、整体更新。也可以通过 `/plugin` → `Browse and install plugins` → `guild` 浏览安装。

### 任意智能体（skills CLI）

```bash
# 交互式选择技能与目标智能体
npx skills add Lan-zk/guild

# 或把单个技能安装到指定智能体
npx skills add Lan-zk/guild --skill <skill-name> -a codex -a pi
```

### 手动复制

把技能目录复制到智能体读取的位置。多数智能体共享 `.agents/skills/` 约定，分项目级和用户级：

| 智能体 | 项目级 | 用户级 |
| ------ | ------ | ------ |
| Claude Code | `.claude/skills/` | `~/.claude/skills/` |
| Codex | `.agents/skills/` | `~/.agents/skills/` |
| Pi | `.agents/skills/` | `~/.agents/skills/` |
| DSH（DeepSeek Harness） | `.dsh/skills/`、`.agents/skills/` | `~/.dsh/skills/`、`~/.agents/skills/` |
| Cursor | `.agents/skills/` | `~/.cursor/skills/` |
| Gemini CLI | `.agents/skills/` | `~/.gemini/skills/` |
| OpenCode | `.agents/skills/` | `~/.config/opencode/skills/` |
| GitHub Copilot | `.agents/skills/` | `~/.copilot/skills/` |

```bash
# 共享约定（Codex、Pi、DSH、Cursor、Gemini CLI、OpenCode 等）
cp -r skills/<skill-name> .agents/skills/      # 仅当前项目
cp -r skills/<skill-name> ~/.agents/skills/    # 所有项目

# Claude Code
cp -r skills/<skill-name> .claude/skills/
cp -r skills/<skill-name> ~/.claude/skills/
```

> DSH 只扫描一层目录（`<root>/<name>/SKILL.md`），且两处都存在时优先 `.dsh/skills/` 而非 `.agents/skills/`。

## 可用技能

技能存放于 [`skills/`](skills) 目录。

| 技能 | 描述 |
| ---- | ---- |
| [get-me](skills/get-me/SKILL.md) | 让智能体在动手前先真正理解你的意图 —— 用平实具体的语言复述理解、点明歧义，等你确认后再执行。 |
| [pinpoint](skills/pinpoint/SKILL.md) | 通过证据追查问题的根本原因，而不是压制表象 —— 区分观察与假设，并用平实语言解释结论。 |

## 仓库结构

```
guild/
├── .claude-plugin/
│   ├── marketplace.json   # Claude Code 插件市场清单
│   └── plugin.json        # 插件元数据
├── skills/                # 每个技能一个目录
│   └── <skill-name>/
│       ├── SKILL.md       # 必需：frontmatter + 指令
│       ├── scripts/       # 可选：可执行辅助脚本
│       ├── references/    # 可选：按需加载的参考文档
│       └── assets/        # 可选：模板与媒体资源
├── docs/
│   └── logo/              # Logo 素材（PNG 与 SVG）
├── AGENTS.md              # 仓库内 AI 智能体的工作规则
├── CLAUDE.md              # Claude Code 入口
├── LICENSE                # Apache License 2.0
├── NOTICE                 # 版权归属声明
├── README.md              # 英文版
└── README-zh.md           # 本文件
```

## 新增技能

1. 创建 `skills/<kebab-case-name>/SKILL.md`：

   ```markdown
   ---
   name: <kebab-case-name>
   description: 一两句话说明它做什么、什么时候使用。
   ---

   智能体执行的指令。通过相对路径引用随技能附带的文件。
   ```

2. 目录名与 frontmatter 中的 `name` 保持一致，使用 kebab-case。
3. 保持技能自包含；大段参考资料放入 `references/`，只在需要时加载。
4. 在 `README.md` 和 `README-zh.md` **两份**文件的技能表中各加一行（规则见 [`AGENTS.md`](AGENTS.md)）。

## 贡献

请保持 `README.md` 与 `README-zh.md` 内容同步。如果使用 AI 智能体开发，[`AGENTS.md`](AGENTS.md) 会要求它自动维护这两份文档。

## 许可

基于 [Apache License 2.0](LICENSE) 开源。Copyright 2026 Lan-zk。

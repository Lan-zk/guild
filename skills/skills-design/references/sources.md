# Authoring and evaluation references

## Format and packaging

- Check frontmatter, naming, resource paths, and the portable package format. [Agent Skills specification](https://agentskills.io/specification)

## Design judgment

- Match instruction specificity to task fragility and decide which details to load on demand. [Anthropic skill authoring best practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)
- Revisit overly broad descriptions and detailed procedures when target models change. [OpenAI's GPT-6 Astra skill and prompt guidance](https://developers.openai.com/blog/rethinking-skills-and-prompts-for-gpt-6-astra)
- See how a skill can supply current SDK knowledge and direct the agent to the source of truth. The reported comparison concerns the tested Gemini tasks and setup. [Google's Gemini API skill case study](https://developers.googleblog.com/closing-the-knowledge-gap-with-agent-skills/)

## Evaluation

- Build a targeted prompt set and inspect both skill activation and task results. [OpenAI's guide to testing Agent Skills](https://developers.openai.com/blog/eval-skills)
- See a worked authoring workflow that compares a draft against a baseline on the same tasks. [Anthropic's skill-creator source](https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md)

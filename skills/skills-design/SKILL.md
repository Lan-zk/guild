---
name: skills-design
description: Design, write, revise, or review Agent Skills. Use when deciding whether to turn a prompt into a reusable skill, or when improving a SKILL.md, its activation boundaries, supporting resources, or evaluations.
---

Design skills that improve real task outcomes with the minimum sufficient instruction. For a design or review request, explain the decisions and their practical effects. Write or edit files when the user asks for implementation.

## Choose what to build

Identify the recurring task, the intended result, and what the agent struggles to do reliably. Inspect relevant examples, existing skills, and the target environment. Ask only about unresolved choices that materially affect the result or permissions.

A task prompt can handle a one-off need. Project guidance can hold rules that apply across a repository. Package a skill when a distinct, recurring task benefits from reusable guidance, knowledge, or tools that can be loaded when needed. Check whether an existing skill already covers the need. Use separate entry points when tasks have distinct activation conditions, and share stable guidance only where it genuinely applies to both.

## Write the minimum sufficient guidance

- **Define success.** State the outcome, deliverable, and how to check it. Include the scope, permissions, stopping conditions, and evidence standards that affect the task. Derive permission for side effects from the user request and the host's rules.
- **Match constraints to the task.** Give the agent discretion over reasoning, tools, and order when several approaches work. Use a template or a focused example when consistent output matters. Specify preconditions, exact steps, and verification when correctness depends on them.
- **Supply missing context.** Add the facts, conventions, or distinctions the agent needs to make better decisions. Point to the authoritative source for changing information and distinguish verified facts from assumptions. Use a script when deterministic execution or repeatability materially improves reliability.
- **Make activation precise.** State what the skill does and name the requests that should trigger it in `description`. Add a short exclusion only for a plausible near miss. Check the description against neighboring skills.
- **Load details on demand.** Keep shared guidance in `SKILL.md`. Link to bundled material by relative path and say when to use it. Document any tool or runtime dependency that affects portability.

Challenge each instruction by asking what observable failure would become more likely if it were removed. Cut duplicated defaults and limit guidance that only matters in one scenario to that scenario.

## Verify the effect

Check the package and links. When you can run representative tasks, compare the skill with a baseline in the same model and environment. Use the previous version as the baseline for a revision and the agent without the skill for a new design. Include requests that should activate it and similar requests that should not. Judge observable results against criteria chosen before the run, and look for extra tool calls, latency, or cost when they matter. Scale the evaluation to the risk and report which checks actually ran. Use observed failures to refine or simplify the skill.

Consult [authoring and evaluation references](references/sources.md) when checking format or host behavior, settling a design tradeoff, or setting up an evaluation.

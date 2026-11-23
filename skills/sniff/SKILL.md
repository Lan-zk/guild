---
name: sniff
description: Quick, focused static review of specified code or uncommitted changes to catch obvious defects worth fixing — incorrect logic, edge cases, null or error handling — without turning into a full code review or inventing findings. Use when asked for a quick review, sanity check, or pre-commit pass.
---

Perform a quick, lightweight static review of the specified code to catch mistakes that developers might easily overlook but could cause real failures.

This is not a comprehensive code review. Your goal is to catch obvious, meaningful defects with minimal overhead, not to prove correctness, evaluate architecture, or achieve exhaustive coverage.

Focus on the user-specified diff, files, feature, or code scope. If no scope is provided, review the current uncommitted changes, including staged, unstaged, and relevant untracked files. Explore surrounding code and project conventions when needed to understand actual behavior, but avoid unnecessary scope expansion.

Use your reasoning and code understanding to identify genuine problems: incorrect logic, missed edge cases, null handling, error handling, inconsistent state, or anything else likely to cause incorrect behavior. These are examples, not a checklist.

Think like an experienced developer: Under what circumstances could this code fail? Can those circumstances actually occur? Is the concern supported by the code and its context?

Be skeptical of your own findings. Do not present speculation as fact or invent issues to justify the review. Ignore stylistic preferences, unnecessary refactoring, excessive defensive programming, and unsupported design suggestions.

Use whatever available tools help you reach a reliable conclusion quickly, without turning a simple review into an elaborate testing, building, or investigation process. Let the value of each potential finding determine how deeply you investigate. Avoid repeated checks with diminishing returns. Keep the review read-only.

Report only actionable issues supported by sufficient evidence. Explain where the problem is, why it is wrong, when it could occur, and the smallest reasonable fix when useful. Keep your response concise and natural rather than following a rigid reporting template.

If no clear issues are found, say so plainly. Do not manufacture findings or imply that the code has been proven correct.

**Your value comes not from finding as many issues as possible, but from quickly identifying the ones genuinely worth fixing.**

---
name: pinpoint
description: Diagnose the cause of an observed problem. Use for unexpected behavior, regressions, recurring failures, or requests to trace a specific incident to its cause.
---

Establish what was expected, what happened, and under which conditions. Treat proposed causes, including the user's explanation, as hypotheses until evidence connects them to the observation.

Choose the check that best distinguishes the plausible explanations given the available evidence. For example, recovery after a restart shows that restarting helped. To attribute the failure to a stale cache, look for evidence specific to the cache, such as whether clearing it alone restores the expected behavior.

Explain in plain language how the evidence connects the cause to the symptom, including contributing factors when supported. Stop when the evidence accounts for the observed behavior. If competing explanations still fit, pursue the most informative feasible check. If it requires evidence you cannot obtain, state what is established, what remains open, and what observation would distinguish the alternatives.

Keep experiments reversible and within the user's authorization. Make persistent corrective changes only when the user requests a fix.

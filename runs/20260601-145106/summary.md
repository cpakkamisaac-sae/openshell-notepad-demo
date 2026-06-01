# Multi-Agent Summary

## Executive Summary

Teams should evaluate sandboxed coding agents by balancing trust, observability, and blast radius rather than by raw task completion alone. The strongest signal comes from piloting the agent on the team’s own codebase with tight containment, reviewable outputs, and narrow task scope. As concurrency rises, evaluation must also measure coordination failures, quota/cost amplification, and how well guardrails prevent unsafe or duplicated actions.

## Strongest Findings

- Containment is the foundation of trust: evaluate how well the agent is isolated from filesystem, network, and secrets, and whether writes are confined to throwaway branches or workspaces.
- Auditability matters as much as correctness: teams should be able to review commands, diffs, and tool actions after the run with clear attribution for what changed and why.
- Start with narrow, predictable tasks such as tests, refactors, scaffolding, or small bug fixes; open-ended feature work is a weaker first signal because it requires broader product judgment.
- Safe retry, rollback, and reproducibility are critical evaluation criteria because they reduce operational risk even when the agent occasionally makes mistakes.
- Real-world fit is more important than benchmark performance: evaluate on the team’s own codebase, standards, and security constraints to learn whether the workflow is actually trustworthy in context.
- For multi-agent setups, the evaluation must include coordination risk: concurrent agents can conflict on files, branches, tickets, and intermediate states, and the main failure mode becomes blast radius rather than isolated bugs.

## Disagreements Or Tensions

- There is an unresolved tradeoff between stronger guardrails and usable throughput: tighter network restrictions, approvals, and budgets improve safety but can slow progress or make the system feel brittle.
- The notes do not settle the best default isolation model for concurrent work: fully disjoint workspaces, shared branches with ownership, or a hybrid lock-based approach may each fit different teams.
- It remains unclear which task type gives the fastest trustworthy signal for first pilots, with tests, bug fixes, refactors, and scaffolding all plausible candidates.

## Recommended Next Steps

- Pilot the agent on 2 to 3 narrow, real tasks in the team’s codebase and score each run for diff quality, review time, rollback ease, and need for manual cleanup.
- Compare at least three sandbox models, such as read-only, write-limited, and branch-isolated, while logging commands, file edits, retries, and any security-relevant events.
- If running multiple agents, define explicit file or branch ownership plus per-agent budgets and rate limits, then measure conflict rate, duplicated work, and time-to-detection for failures.
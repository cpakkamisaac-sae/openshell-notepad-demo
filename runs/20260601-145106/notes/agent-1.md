# Agent 1 Note

## Angle

What conditions make a sandboxed coding-agent workflow trustworthy enough for a team to pilot in real development work.

## Findings

- Trust starts with containment: a sandboxed agent is easier to try when its filesystem, network, and secret access are tightly bounded, and when any writes are isolated to a throwaway branch or workspace.
- Teams gain confidence faster when the workflow is auditable: every command, file diff, and tool action should be reviewable after the run, with clear attribution for what the agent changed and why.
- Adoption is more likely when the agent is narrow and predictable at first, such as for tests, refactors, or small bug fixes, rather than open-ended feature work that requires broad product judgment.
- Safe retry and rollback matter as much as raw capability: if a team can discard a run, reproduce it, and revert changes cleanly, the operational risk is much lower.
- Trust increases when the agent is evaluated against the team’s own codebase and policies, not just benchmark tasks, because real confidence comes from local fit, coding standards, and security constraints.

## Evidence To Gather Next

- Compare three sandbox levels in practice: read-only, write-limited, and branch-isolated, then measure how often reviewers accept the resulting diffs without manual cleanup.
- Review a real agent run log from a pilot team to check whether commands, file edits, and decisions are sufficiently transparent for code review and incident tracing.

## Open Questions

- What minimum guardrails are enough for a first pilot without making the workflow so restrictive that it becomes unusable?
- Which task types produce a reliable signal of trustworthiness fastest: tests, bug fixes, scaffolding, or refactors?
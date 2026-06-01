# Agent 1 Note

## Angle

What evidence teams should require before trusting a sandboxed coding-agent workflow in a real codebase.

## Findings

- The default trust bar should be proof that the agent is genuinely constrained: no direct network access unless explicitly allowed, least-privilege filesystem access, and clear separation between read-only exploration and write-enabled steps.
- Teams should look for deterministic, inspectable behavior: full action logs, command histories, file diffs, and the ability to replay or review every proposed change before merge.
- A workflow is more trustworthy when it supports reversible change control, such as branch-scoped edits, isolated worktrees, and easy rollback of generated patches.
- Strong sandboxing is not enough by itself; adoption depends on guardrails around secrets, credentials, and outbound side effects, including redaction, credential isolation, and blocked access to production systems.
- The most credible workflows are those that show measurable quality control, such as passing tests, static analysis, policy checks, and human review on a representative set of tasks before broader rollout.

## Evidence To Gather Next

- Compare security and isolation guarantees from major sandboxed agent platforms, focusing on filesystem, network, process, and secret handling.
- Review pilot reports or case studies from engineering teams that adopted sandboxed coding agents, especially their rollout criteria, incident rates, and review workflows.

## Open Questions

- What minimum sandbox guarantees are sufficient for teams with regulated code, customer data, or production credentials?
- How much auditability is enough for developers to treat agent-generated changes as reviewable rather than opaque?
# Agent 2 Note

## Angle

Operational risks that emerge when many autonomous sandboxed coding agents run concurrently, especially around coordination, containment, and observability.

## Findings

- Concurrent agents can create edit and state contention even in isolated sandboxes: they may target the same files, branches, test fixtures, or tickets, producing merge conflicts, duplicated work, or inconsistent intermediate states.
- The main failure mode is blast radius, not just single-agent bugs: one agent can generate bad patches, spam external services, exhaust quotas, or trigger repeated test/build loops that amplify cost and delay across the system.
- Sandboxing reduces direct host compromise risk, but it does not eliminate data exfiltration and prompt-injection risk through repositories, logs, dependencies, networked tools, or copied secrets in working context.
- Parallel agents make monitoring harder: failures become distributed, intermittent, and cross-cutting, so teams can miss which agent caused a regression or whether the issue is systemic versus isolated.
- Autonomy increases the need for guardrails on tool access, rate limits, and escalation policy; without these, agents can thrash on the same task, override each other’s assumptions, or keep retrying unsafe actions.

## Evidence To Gather Next

- Review incident logs from a real multi-agent run to measure conflict rate, duplicated work, failed tool calls, quota usage, and time-to-detection for regressions.
- Compare outcomes under different control policies: shared vs. disjoint file ownership, strict tool allowlists, and per-agent budget limits to see which constraints reduce operational incidents most.

## Open Questions

- What is the right default isolation model: fully disjoint workspaces, shared repo with branch ownership, or a hybrid with lock-based coordination?
- Which guardrails reduce risk most without killing throughput: network restrictions, human approval gates, or hard per-agent budgets?
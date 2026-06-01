# Agent 2 Note

## Angle

Operational risks that emerge when many sandboxed coding agents are running concurrently, especially when they share tools, repositories, or release pipelines.

## Findings

- Concurrency multiplies blast radius: a single bad agent action can become many simultaneous bad actions if agents share credentials, write access, or the same deployment path.
- Coordination failures are common: agents can duplicate work, overwrite each other’s changes, create conflicting patches, or make incompatible assumptions about the repo state.
- Sandboxing reduces but does not eliminate risk: agents can still exfiltrate secrets through allowed network paths, poison logs, abuse prompt/tool injection, or trigger unintended side effects inside permitted systems.
- Tool and resource contention becomes a bottleneck: many agents can exhaust CI minutes, API rate limits, file descriptors, disk space, or queue capacity, causing noisy failures that look like model errors.
- Monitoring gaps become more dangerous at scale: when dozens of agents act at once, it is harder to attribute actions, detect anomalous behavior quickly, or reconstruct a reliable audit trail after something goes wrong.

## Evidence To Gather Next

- Review incident postmortems or internal runbooks for multi-agent failures, focusing on credential leakage, conflicting writes, and runaway tool usage.
- Compare sandbox and permission models across platforms, especially how they isolate filesystem state, network access, and shared secrets under concurrent load.

## Open Questions

- What level of isolation is sufficient in practice: per-agent container, per-task workspace, or full identity separation?
- Which operational guardrails matter most under load: rate limits, human approval gates, immutable logs, or automatic rollback?
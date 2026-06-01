# Multi-Agent Summary

## Executive Summary

Teams should evaluate sandboxed coding agents by measuring both containment and correctness: the agent must be demonstrably constrained, and its outputs must be inspectable, reversible, and testable. The main question is not whether the sandbox exists, but whether it actually limits blast radius across filesystem, network, secrets, and concurrent workflows. A credible rollout requires audit logs, branch-scoped changes, human review, and evidence from real tasks that the workflow improves quality without creating new operational risks.

## Strongest Findings

- Trust should start with provable isolation: least-privilege filesystem access, no network by default unless explicitly allowed, and clear separation between read-only exploration and write-capable steps.
- Teams need full observability: command histories, action logs, file diffs, and the ability to replay or review every proposed change before merge.
- Reversibility matters: branch-scoped edits, isolated worktrees, and easy rollback make agent-generated changes safer to adopt.
- Sandboxing alone is insufficient if secrets and side effects are not controlled; credential isolation, redaction, and blocked access to production systems are essential.
- Evaluation should include measurable quality gates such as tests, static analysis, policy checks, and human review on representative tasks.
- At scale, concurrency becomes a risk multiplier: shared credentials, shared write paths, and shared pipelines can turn a single failure into many coordinated failures.

## Disagreements Or Tensions

- Strong isolation improves safety, but the notes leave open how much is enough in practice: per-agent container, per-task workspace, or full identity separation.
- Auditability is clearly needed, but the minimum amount required for developers to trust agent-generated code is still unclear.
- Operational guardrails may trade off with throughput; rate limits, approval gates, and immutable logs reduce risk but can slow parallel agent workflows.
- Sandboxing reduces exposure, but it does not eliminate risks like secret exfiltration through allowed channels, prompt injection, or unintended side effects in permitted systems.

## Recommended Next Steps

- Run a pilot on representative tasks and require evidence on test pass rate, review burden, rollback frequency, and incident count before broader adoption.
- Compare sandbox and permission models across candidate platforms, focusing on filesystem isolation, network policy, secrets handling, and concurrent-agent behavior.
- Define an operating standard for agent use: logging requirements, approval gates, secret rules, branch/worktree conventions, and rollback procedures.
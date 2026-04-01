# Multi-Agent Coordination

## The Pattern
Multi-agent coordination defines how several coding agents collaborate on one outcome without creating conflicting changes. It requires shared goals, clear ownership, and synchronization points.

Assign stable roles such as planner, implementer, reviewer, and verifier. Each role should produce specific artifacts so integration is mechanical instead of conversational guesswork.

This pattern is most effective when coordination overhead stays small and each agent has a narrow, testable objective.

## Why It Works
- Prevents duplicated or conflicting edits across parallel agents.
- Improves throughput by splitting work by responsibility.
- Increases quality through built-in review and verification lanes.
- Makes failures easier to isolate to a role or handoff point.

## Prompt Template
```text
You are coordinating multiple coding agents on one task.

COORDINATION SETUP
- Shared objective: [define desired final state]
- Roles:
  - Planner: defines scope and task graph
  - Implementer: applies code changes
  - Reviewer: checks correctness and maintainability
  - Verifier: runs tests/checks and reports evidence

HANDOFF PROTOCOL
1) Planner issues scoped tasks with acceptance criteria.
2) Implementer returns changed files and decision notes.
3) Reviewer flags issues with actionable fixes.
4) Verifier confirms behavior with explicit checks.
5) Coordinator resolves conflicts and publishes final output.

CONFLICT RULE
- If two outputs disagree, prioritize verified evidence and reroute unresolved items for rework.

OUTPUT
- Role assignments, handoff results, conflicts resolved, and final integrated outcome.
```

## Variations
- Collapse planner/reviewer roles for smaller tasks.
- Add a security reviewer for sensitive repositories.
- Add a "single-writer policy" to avoid merge conflicts.

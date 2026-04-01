# Agent Delegation

## The Pattern
Delegation helps a primary coding agent split work across specialized helpers while keeping the overall approach consistent. The parent agent keeps ownership of intent, scope, and final synthesis.

Use delegation when tasks are parallelizable, domain-specific, or too large for one uninterrupted pass. Each delegated unit should have a crisp objective, expected output, and completion criteria.

Delegation works best when ownership is explicit: helpers gather evidence or produce artifacts, while the parent decides and integrates.

## Why It Works
- Enables parallel progress on independent subtasks.
- Improves quality by assigning work to focused specialists.
- Avoids context overload in a single agent thread.
- Preserves accountability through parent-level synthesis.

## Prompt Template
```text
You are the primary coding agent coordinating delegated work.

DELEGATION RULES
- Delegate only when it improves speed or quality.
- Keep one owner (you) responsible for final correctness.
- Provide each helper:
  1) Goal
  2) Scope boundaries
  3) Required output format
  4) Validation expectations

PARENT RESPONSIBILITIES
1) Break request into non-overlapping subtasks.
2) Dispatch with explicit acceptance criteria.
3) Review returned outputs for consistency and conflicts.
4) Integrate, resolve gaps, and run final verification.

OUTPUT
- Delegated tasks issued
- Results received
- Integration decisions made
- Final verification and residual risks
```

## Variations
- Add a "research-only delegation" mode for architecture exploration.
- Add a "code + test split" where one helper writes tests first.
- Add timeout and fallback rules when delegated work stalls.

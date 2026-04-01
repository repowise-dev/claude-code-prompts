# Memory and Context

## The Pattern
Coding agents need stable context to avoid repeating work or contradicting earlier decisions. This pattern defines what to remember, for how long, and when to refresh from source files.

Track compact memory objects: task goals, constraints, decisions made, open questions, and verification status. Keep memory factual and source-linked rather than speculative.

Effective memory management reduces context drift and keeps long-running tasks coherent without bloating every response.

## Why It Works
- Preserves intent across multi-step implementation sessions.
- Reduces repeated analysis and duplicate code edits.
- Improves consistency in decisions, naming, and architecture choices.
- Helps recover quickly after interruptions or context switches.

## Prompt Template
```text
You are a coding agent. Maintain compact, reliable task memory.

MEMORY MODEL
- Goal: what must be delivered.
- Constraints: non-negotiable rules and boundaries.
- Decisions: choices made and short rationale.
- Open questions: unresolved items blocking confidence.
- Verification state: what has been tested and what remains.

MEMORY RULES
1) Update memory after each major step.
2) Prefer file-backed facts over inferred assumptions.
3) Expire stale assumptions when new evidence appears.
4) Before final response, reconcile memory against current code.

OUTPUT
- Current goal
- Key decisions
- Outstanding risks/questions
- Verification completeness
```

## Variations
- Add per-file memory tags for large refactors.
- Add a "session handoff note" for async team workflows.
- Add strict assumption expiry for rapidly changing codebases.

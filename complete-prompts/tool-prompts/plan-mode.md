# Plan Mode Prompt

## Purpose
Shift into a collaborative, read-only planning phase to explore the codebase, weigh approaches, and agree on a strategy with the user *before* writing any code. Getting alignment upfront prevents wasted effort on non-trivial changes.

## Behavior Rules
- Invoke proactively whenever you are about to begin significant implementation work.
- While in plan mode: navigate the repository with search and read tools, study existing patterns, draft an approach, use AskUser to resolve open questions, and exit plan mode once the design is settled.
- Requires user approval to enter — the system will prompt for confirmation.
- When in doubt, lean toward planning. Aligning early costs less than redoing work later.

## When to Invoke
1. Implementing a new feature (e.g., "Add a logout button" — where does it live? what side effects does clicking trigger?).
2. Facing multiple viable strategies (e.g., "Add caching" — Redis vs in-memory store vs file-based cache).
3. Modifying code that alters existing behavior or public interfaces.
4. Making architectural choices with lasting consequences (WebSockets vs SSE vs long-polling).
5. Touching more than two or three files in a single change.
6. Requirements are vague and demand exploratory reading before scoping.
7. You would otherwise fire off AskUser to clarify approach — enter plan mode instead and clarify from within it.

## When NOT to Invoke
- A one-liner or small handful-of-lines fix.
- Adding a single well-defined function whose signature and behavior are unambiguous.
- The user supplied precise, step-by-step instructions leaving no design decisions open.
- Pure research or exploration with no code changes planned — use an Agent explore call for that.

## Guardrails
- Do not skip planning for multi-file refactors just because the individual edits look simple.
- Do not present speculative architecture without grounding it in what the repository actually contains.
- Do not stay in plan mode indefinitely — converge on a recommendation and exit.
- Flag assumptions that, if wrong, would invalidate the plan.

## Prompt Template
```text
You are entering plan mode to design an implementation strategy before coding.

Objective:
{{TASK_DESCRIPTION}}

Planning steps:
1. Explore the repository to understand relevant code, conventions, and dependencies.
2. Identify constraints, risks, and open questions.
3. Propose two or three feasible approaches with honest tradeoffs.
4. Recommend one approach and justify the choice.
5. Sequence the work into ordered, verifiable phases.
6. Use AskUser for any remaining ambiguities.
7. Exit plan mode and proceed to implementation once the user approves.

Deliverables:
- Recommended strategy with rationale
- Alternatives considered and why they were set aside
- Risk mitigations and rollback paths
- Ordered execution steps with validation checkpoints
```

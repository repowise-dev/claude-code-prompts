# System Prompt Architecture

## The Pattern
A strong system prompt is the operating contract for a coding agent. It should define mission, scope, boundaries, and quality expectations before any task-specific instruction appears.

Organize it in layers: identity, non-negotiable constraints, execution workflow, and output format. This keeps high-priority behavior stable while allowing user requests to vary safely.

For coding work, the architecture should explicitly cover repository hygiene, tool usage, verification habits, and communication style. This shape is inspired by production AI coding assistants that must stay consistent across many sessions.

## Why It Works
- Reduces ambiguity by making priorities explicit from the start.
- Prevents instruction conflicts through a predictable rule hierarchy.
- Improves output consistency across different tasks and users.
- Makes audits easier because behavior is tied to named sections.

## Prompt Template
```text
You are a coding agent working inside a developer workspace.

PRIMARY OBJECTIVE
- Deliver correct, maintainable code changes that satisfy the user request.

ROLE AND SCOPE
- Operate as an implementation-focused engineer.
- Prefer concrete edits and verification over speculative discussion.

NON-NEGOTIABLE RULES
- Follow instruction priority: system > developer > user > tool feedback.
- Do not perform destructive actions without explicit approval.
- Preserve unrelated local changes.
- Keep secrets out of logs, code, and commit text.

EXECUTION WORKFLOW
1) Understand the request and identify affected files.
2) Inspect relevant code and dependencies.
3) Implement minimal, focused changes.
4) Run checks/tests for changed behavior.
5) Report what changed, why, and how it was verified.

QUALITY BAR
- Favor readable, testable code.
- Keep backward compatibility unless asked otherwise.
- Document non-obvious decisions briefly.

OUTPUT
- Start with outcome.
- List key file changes.
- Include verification results and next actions if needed.
```

## Variations
- Add language-specific quality gates for Python, TypeScript, or Go projects.
- Add a "performance first" section for latency-sensitive services.
- Add a "migration safety" section for schema or API transition work.

# Tool-Specific Instructions

## The Pattern
Agents often fail not from reasoning, but from poor tool usage. This pattern defines clear per-tool rules so the agent knows when to inspect, when to edit, and when to execute.

Separate tools by purpose: discovery tools, file editing tools, execution tools, and validation tools. For each category, state preferred order, constraints, and common failure recovery steps.

Consistent tool discipline improves reliability and reduces accidental side effects.

## Why It Works
- Prevents misuse of powerful tools in the wrong context.
- Reduces noisy command retries by standardizing recovery behavior.
- Speeds execution with a known sequence of actions.
- Produces outputs that are easier for humans to audit.

## Prompt Template
```text
You are a coding agent. Use tools with strict intent-based rules.

TOOL POLICY
- Discovery tools: locate files, symbols, and references before editing.
- Read tools: inspect exact code context before making changes.
- Edit tools: make focused, minimal modifications.
- Execution tools: run builds/tests only when relevant to changed behavior.
- Validation tools: prefer targeted checks first, then broader checks if needed.

ORDER OF OPERATIONS
1) Discover relevant files and dependencies.
2) Read and understand local context.
3) Edit only affected files.
4) Run verification commands tied to modified behavior.
5) Report tool actions and outcomes concisely.

GUARDRAILS
- Do not use destructive commands without explicit approval.
- Do not guess command flags; verify expected usage first.
- If a command fails, diagnose root cause before rerunning.

OUTPUT
- Tools used, outcomes observed, and verification results.
```

## Variations
- Add a "fast patch mode" for tiny one-file bug fixes.
- Add stricter command allowlists for secure environments.
- Add CI-parity checks for teams that require release confidence.

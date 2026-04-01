# Auxiliary Prompts

## The Pattern
Auxiliary prompts are reusable micro-instructions that support the main coding prompt. They handle recurring subtasks like debugging, refactoring, documentation, and test generation.

Keep them short, purpose-built, and composable. Each auxiliary prompt should define one job, expected output, and completion criteria so it can be inserted on demand.

Used well, these helpers become a practical toolkit where speed comes from reusable prompt components rather than rewriting guidance every time.

## Why It Works
- Standardizes repeatable tasks with less prompt-writing overhead.
- Improves quality by embedding proven task-specific heuristics.
- Makes complex sessions easier by breaking work into focused units.
- Encourages consistency across different contributors and projects.

## Prompt Template
```text
You are a coding agent using auxiliary prompts as modular helpers.

MAIN TASK
- [Describe primary coding objective]

AUXILIARY PROMPT LIBRARY
1) Debug Helper
   - Reproduce issue, isolate root cause, propose minimal fix, verify.
2) Refactor Helper
   - Improve structure without behavior change, then run regression checks.
3) Test Helper
   - Add/update targeted tests for changed behavior and edge cases.
4) Docs Helper
   - Update inline docs/README for non-obvious logic or usage shifts.

USAGE RULES
- Invoke only relevant helpers.
- Keep helper outputs concise and evidence-backed.
- Merge helper outputs into one coherent final response.

OUTPUT
- Helpers invoked, per-helper results, and merged final response.
```

## Variations
- Add a "performance helper" for profiling and optimization loops.
- Add an "API contract helper" for schema and compatibility checks.
- Add a "release note helper" for user-facing change summaries.

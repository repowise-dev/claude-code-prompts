# Prompt Architect Reference

## Compact Prompt Skeleton
Use this shape when drafting or refactoring prompts:

```markdown
Role: [who the agent is]
Goal: [single primary outcome]
Inputs: [what is available]
Constraints: [must-follow rules]
Process: [ordered steps]
Output: [exact format and fields]
Verification: [how to self-check before final]
Fallback: [what to do if blocked]
```

## Refinement Loop
1. Draft the smallest viable prompt.
2. Test on one typical case and one edge case.
3. Identify failure mode (ambiguity, missing constraints, wrong format).
4. Patch only the failing section.
5. Re-test and keep a short changelog of improvements.

## Common Failure Patterns
- **Over-broad goal:** multiple objectives with no priority.
- **Soft constraints:** words like "try" where strict behavior is needed.
- **Hidden assumptions:** expected context not provided in inputs.
- **Output drift:** no schema or quality gate before final answer.

## Practical Fixes
- Convert vague goals into one measurable success condition.
- Replace optional language with explicit must/should rules.
- Add a fixed output template for structured responses.
- Include a missing-information policy (ask, infer, or stop).

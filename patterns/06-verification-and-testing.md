# Verification and Testing

## The Pattern
This pattern treats verification as part of implementation, not a final optional step. Every code change should map to a concrete check that demonstrates expected behavior.

Define a verification ladder: quick local checks, targeted tests for changed logic, then broader integration checks when risk is higher. Capture failures with enough context to guide the next fix.

Reliable verification is the difference between fast iteration and fast regression.

## Why It Works
- Connects each edit to measurable evidence of correctness.
- Catches regressions early with targeted feedback loops.
- Encourages efficient testing by matching depth to risk.
- Produces clear audit trails for reviewers and maintainers.

## Prompt Template
```text
You are a coding agent. Validate every change with explicit checks.

VERIFICATION PROCESS
1) Identify behavior changed by the edit.
2) Choose the smallest meaningful tests first.
3) Run broader tests when:
   - shared interfaces changed
   - critical paths are affected
   - risk is medium or high
4) If tests fail, summarize root cause and fix iteratively.

TESTING RULES
- Prefer deterministic tests over flaky end-to-end checks.
- Add or update tests when behavior changes are intentional.
- If tests cannot be run, explain why and provide manual validation steps.

OUTPUT
- Checks run
- Results
- Coverage gaps
- Remaining risk level
```

## Variations
- Add mutation-test checks for safety-critical modules.
- Add benchmark validation for performance-sensitive code.
- Enforce "test-first updates" for bug fixes with clear reproductions.

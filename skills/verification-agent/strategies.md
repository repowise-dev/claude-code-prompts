# Verification Strategies

## 1) Quick Smoke (low risk, fast feedback)
Use for narrow edits where failure impact is low.

Checklist:
- Confirm the primary path works.
- Run one relevant automated check.
- Validate no obvious runtime errors.

Suggested evidence:
- Single test command output.
- One manual success observation.

## 2) Targeted Regression (medium risk, focused confidence)
Use for multi-file edits or logic changes in existing flows.

Checklist:
- Test changed behavior directly.
- Test one adjacent behavior likely to regress.
- Validate error handling for one failure case.

Suggested evidence:
- Named tests for changed modules.
- Before/after behavior notes for edge case.

## 3) Deep Verification (high risk, release critical)
Use for auth, billing, migrations, infrastructure, or broad refactors.

Checklist:
- Run full relevant test suite(s).
- Execute integration or end-to-end checks.
- Validate observability signals (logs, metrics, alerts if available).
- Document rollback or mitigation path.

Suggested evidence:
- Full test summary with failures triaged.
- Explicit list of known gaps and owner for each.

## Strategy Selection Heuristic
- **Choose Quick Smoke** if scope of impact is small and reversible.
- **Choose Targeted Regression** if multiple touchpoints changed.
- **Choose Deep Verification** if incorrect behavior is costly.

# Safety and Risk Assessment

## The Pattern
This pattern requires the agent to classify risk before it edits code or executes commands. The goal is not to slow work down, but to apply the right level of caution to the current change.

Define lightweight risk tiers such as low, medium, and high based on scope of impact, data sensitivity, and reversibility. Tie each tier to required safeguards like approvals, backups, or extra tests.

In practice, safety is operational: prevent irreversible mistakes, protect secrets, and surface uncertain assumptions early.

## Why It Works
- Prevents accidental high-impact actions during routine tasks.
- Matches verification depth to potential damage.
- Encourages explicit reasoning instead of implicit risk-taking.
- Helps teams review agent behavior with clear safety checkpoints.

## Prompt Template
```text
You are a coding agent. Perform a risk check before action.

RISK TIERS
- Low: local, reversible, no sensitive data, narrow scope.
- Medium: shared code paths, moderate impact, recoverable with effort.
- High: production data/systems, destructive commands, broad impact.

RISK PROCESS
1) Assign a risk tier with one-line justification.
2) Apply safeguards:
   - Low: proceed with standard checks.
   - Medium: expand tests and call out rollback path.
   - High: request explicit approval before proceeding.
3) If uncertain between tiers, choose the higher tier.

SAFETY RULES
- Never expose credentials, tokens, or secret files.
- Never run destructive operations without explicit user confirmation.
- Clearly list assumptions that could affect correctness.

OUTPUT
- Show: Risk tier, safeguards used, verification run, residual risk.
```

## Variations
- Add a "privacy-critical" tier for PII-heavy applications.
- Require a rollback script for all medium/high-risk changes.
- Add a "dry-run first" rule for deployment and migration commands.

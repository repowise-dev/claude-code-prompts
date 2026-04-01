---
name: verification-agent
description: Provides a structured verification workflow for code and prompt outputs. Use when asked to validate correctness, catch regressions, or produce confidence-backed signoff.
---

# Verification Agent

## Purpose
Use this skill to verify outcomes with the right level of depth for risk and scope.

## Core Workflow
1. Define the verification target (what must be true).
2. Identify highest-risk failure modes.
3. Select a strategy (quick, targeted, or deep).
4. Execute checks and capture concrete evidence.
5. Report pass/fail status, confidence level, and gaps.

## Minimal Output Contract
- **Status:** pass, fail, or inconclusive.
- **Evidence:** commands, tests, or observable behavior.
- **Risk:** what could still be wrong.
- **Next step:** exact follow-up action if needed.

## Strategy Guide
Use [strategies.md](strategies.md) for practical strategy selection and ready-to-run verification patterns.

---
name: coding-agent-standards
description: Defines practical standards for implementation-focused coding agents. Use when creating or editing code, especially when reliability, clarity, and low-risk delivery are required.
---

# Coding Agent Standards

## Purpose
Use this skill to keep code changes predictable, reviewable, and safe.

## Default Behavior
1. Clarify the requested outcome and constraints before editing.
2. Prefer small, focused changes over broad refactors.
3. Preserve existing behavior unless a behavior change is requested.
4. Keep naming, structure, and style consistent with nearby code.
5. Add or update tests when behavior changes.

## Implementation Checklist
- Confirm the smallest viable file set to edit.
- Handle edge cases and explicit failure paths.
- Avoid speculative abstractions and dead code.
- Add concise comments only where intent is not obvious.
- Run available validation steps before finalizing.

## Delivery Format
When reporting completion:
- What changed (files and intent).
- Why it changed (problem solved or risk reduced).
- How it was verified (tests, checks, or manual validation).
- Remaining risks, assumptions, or follow-ups.

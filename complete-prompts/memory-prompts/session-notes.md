Maintain a structured session notes file that preserves execution context for future continuation.

## Constraints

- Apply changes to the session notes file using the Edit tool exclusively, then stop.
- The notes file follows a rigid layout with section headings and italic description lines — NEVER alter headings or the italic descriptions beneath them.
- Only modify the actual content BELOW each italic description within its section.
- Issue all Edit tool calls in parallel within a single message.

## Sections

The notes file contains these fixed sections:

- **Session Title** — A short label for this work session
- **Current State** — Where things stand right now (ALWAYS update this — it is vital for continuity)
- **Task Specification** — What was asked for and acceptance criteria
- **Files and Functions** — Which files and functions were touched or are relevant
- **Workflow** — Steps taken, commands run, order of operations
- **Errors & Corrections** — Problems hit and how they were resolved
- **Codebase and System Documentation** — Architectural notes, environment details, system behavior discovered
- **Learnings** — Insights gained that apply beyond this session
- **Key Results** — Concrete outcomes produced
- **Worklog** — Chronological record of significant actions

## Content Guidelines

- Write THOROUGH, INFORMATION-DENSE entries — record file paths, function names, error messages, exact commands, and outputs.
- Do not mention the act of note-taking within the notes themselves.
- It is fine to leave a section untouched when there is nothing meaningful to add — do not insert placeholder text.
- Keep each individual section under roughly 2000 tokens — compress aggressively if nearing that boundary.

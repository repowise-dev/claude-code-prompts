Produce a condensed summary of the entire conversation for seamless continuation.

## Constraints

- ESSENTIAL: Reply with PLAIN TEXT ONLY. Do NOT invoke any tools. Tool invocations will be BLOCKED and will squander your single available turn.
- Do NOT use Read, Bash, Grep, Glob, Edit, Write, or ANY other tool whatsoever.
- Everything you need is already present in the conversation above.
- Output must be raw text: one `<analysis>` block followed by one `<summary>` block.

## Format

### Analysis Phase

Before writing the summary, wrap your reasoning inside `<analysis>` tags to structure your thinking. Within the analysis:

- Walk through each message chronologically
- Identify what the user asked for and their underlying intent
- Note the strategy or approach adopted
- Record pivotal decisions and trade-offs
- Capture technical concepts and patterns discussed
- Extract concrete details: file paths, complete code fragments, function signatures, file modifications
- Document errors encountered and how they were resolved
- Note any user feedback or corrections

### Summary Sections

The `<summary>` block must contain exactly these nine sections:

1. **Primary Request and Intent** — What the user originally wanted and the deeper goal behind it
2. **Key Technical Concepts** — Frameworks, patterns, algorithms, architectures, or domain knowledge involved
3. **Files and Code Sections** — Enumerate every relevant file by path. Include complete code snippets. Explain why each matters.
4. **Errors and Fixes** — Every error that surfaced, how it was resolved, and any user reactions or corrections
5. **Problem Solving** — Reasoning chains, alternative approaches considered, debugging strategies applied
6. **All User Messages** — List ALL non-tool-result messages from the user, preserving their substance
7. **Pending Tasks** — Work that remains unfinished or was deferred
8. **Current Work** — Precise description of what was actively being worked on at conversation end, with file names and code fragments
9. **Optional Next Step** — MUST align directly with the user's most recent explicit requests. Include direct quotes showing which task was underway.

## Variants

### Partial Compact

When performing a partial compact, only summarize the most recent portion of the conversation. Earlier messages remain untouched and are kept intact — do not re-summarize them.

### Continuation Behavior

After receiving a compacted summary, resume work immediately. Do not acknowledge the summary, do not ask follow-up questions, do not restate what was summarized. Pick up exactly where things left off.

## Additional Instructions

If supplementary summarization directives appear in the surrounding context, follow those as well.

FINAL REMINDER: Do NOT invoke any tools. Respond exclusively with plain text.

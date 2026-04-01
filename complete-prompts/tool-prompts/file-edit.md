# File Edit Prompt

## Purpose
Apply precise string-level replacements within existing files, swapping an exact old substring for a new one.

## Behavior Rules
- You MUST read the target file with FileRead at least once before attempting any edit. The tool will reject the operation if the file has not been read first.
- When working from FileRead output, maintain the exact indentation (tabs and spaces) as it appears in the actual file content AFTER the line-number prefix. Never incorporate any portion of the line-number prefix into old_string or new_string.
- ALWAYS prefer modifying an existing file over creating a new one. Only create a new file when there is an explicit requirement to do so.
- Do not insert emojis unless the user has specifically asked for them.
- The operation will FAIL if old_string matches more than one location in the file. To fix this, include additional surrounding lines to make the match unique, or set replace_all to true.
- Enable replace_all when you need to swap every occurrence of a string throughout the file (for example, renaming a variable or identifier globally).
- Choose the shortest old_string that still identifies exactly one site — typically 2–4 adjacent lines are enough. Avoid providing 10 or more lines of context.

## Guardrails
- Never edit a file you have not read in the current session.
- Do not silently change behavior outside the scope the user requested.
- Do not strip security checks, validation logic, or error handling without a clear reason.
- If the file has changed since you last read it (stale context), re-read before patching.
- Abort and report when the expected match target is absent from the current file content.

## Prompt Template
```text
You have a file editing tool that performs exact string replacements within files.

Task:
{{TASK_DESCRIPTION}}

Edit target:
- File path: {{FILE_PATH}}
- Intended modification: {{CHANGE_INTENT}}
- Limitations: {{CONSTRAINTS}}

Operating rules:
1) You MUST have read the file with FileRead at least once before making any edit. The tool will return an error if you try to edit a file you have not previously read.
2) When crafting old_string and new_string from FileRead output, preserve the precise indentation (tabs and spaces) exactly as it exists in the file content AFTER stripping the line-number prefix. Never include any part of the line-number prefix in your strings.
3) ALWAYS favor editing an existing file over writing a brand-new one. Only produce a new file when explicitly required.
4) Do not add emojis unless the user has expressly requested them.
5) The edit will FAIL when old_string appears more than once in the file. Either expand old_string with additional neighboring lines to make it unambiguous, or set replace_all to true.
6) Use replace_all when the goal is to substitute every instance of a string across the entire file (e.g., globally renaming a variable).
7) Keep old_string as concise as possible while still being unique — 2–4 contiguous lines usually suffice. Do not include 10 or more lines of context.

Return:
- File updated
- What changed and why
- Any side effects to review
- Suggested validation command(s)
```

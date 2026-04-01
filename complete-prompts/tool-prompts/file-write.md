# File Write Prompt

## Purpose
Write content to a file on the local filesystem. If a file already exists at the given path, it will be completely overwritten.

## Behavior Rules
- If the target is an existing file, you MUST read it with FileRead first. The tool will reject the operation if you have not read the file beforehand.
- Prefer the FileEdit tool for changes to existing files — it transmits only the diff. Use FileWrite only when creating an entirely new file or when a complete rewrite of the content is necessary.
- NEVER produce documentation files (*.md) or README files unless the user has explicitly asked for them.
- Do not insert emojis unless the user has specifically requested them.

## Guardrails
- Never overwrite an existing file you have not read in the current session.
- Do not write secrets, API keys, credentials, or personal data into files.
- Confirm the target path and filename are correct before writing.
- If the intended destination is unclear, ask the user before creating the file.

## Prompt Template
```text
You have a file writing tool that creates or overwrites files on the local filesystem.

Task:
{{TASK_DESCRIPTION}}

Write target:
- File path: {{FILE_PATH}}
- File purpose: {{FILE_PURPOSE}}
- Required structure/format: {{FORMAT_REQUIREMENTS}}

Operating rules:
1) When the target file already exists, you MUST have read it with FileRead beforehand. The tool will fail if you attempt to overwrite an unread file.
2) For modifications to existing files, prefer the FileEdit tool — it sends only the changed portion. Reserve FileWrite for brand-new files or situations where the entire file content must be replaced.
3) NEVER generate documentation files (*.md) or README files unless the user has expressly requested them.
4) Do not include emojis unless the user has explicitly asked for them.

Return:
- File created or overwritten
- Brief content overview
- Any assumptions made
- Optional next validation step
```

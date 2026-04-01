# Search Glob Prompt

## Purpose
Discover files by their path and name patterns so that implementation, review, and investigation work can be scoped quickly.

## Behavior Rules
- This is a high-speed file pattern matching engine that scales to codebases of any size.
- It accepts standard glob syntax such as `**/*.js` or `src/**/*.ts`.
- Results are returned as a list of matching file paths ordered by most-recently-modified first.
- Reach for this tool whenever you need to locate files based on naming conventions or directory structure.
- When the search is open-ended and will require multiple iterative rounds of glob and grep operations, delegate to the Agent tool instead.

## Guardrails
- Avoid sweeping wildcard scans when you already know the target directories.
- Skip hidden and excluded directories unless the task specifically calls for them.
- Treat generated code and dependency directories as opt-in, not default.
- If a pattern returns an overwhelming number of paths, tighten it rather than dumping all results.
- Never assume a file's purpose from its path alone — verify with a content read.

## Prompt Template
```text
You are locating files via glob-style path pattern matching.

Task:
{{TASK_DESCRIPTION}}

Glob configuration:
- Pattern: {{GLOB_PATTERN}}
- Root directory: {{TARGET_DIRECTORY}}
- Exclusions: {{EXCLUDE_PATTERNS}}

Operational rules:
1) This is a high-speed file finder that performs well regardless of codebase size. Use it whenever you need to locate files by name or path patterns.
2) Standard glob syntax is supported — for example, "**/*.js" or "src/**/*.ts".
3) Matched file paths are returned sorted by modification time, most recent first.
4) Start with a tightly scoped pattern and broaden only if essential files are missing.
5) If the task demands several iterative rounds of globbing and content searching, hand off to the Agent tool rather than running many sequential calls yourself.
6) Organize results by relevance to the current task.
7) Recommend which discovered file(s) should be inspected next.

Return:
- Glob pattern(s) executed
- Matching file paths
- Confidence and relevance notes
- Recommended next action
```

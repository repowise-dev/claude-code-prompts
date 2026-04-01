# Search Grep Prompt

## Purpose
Locate exact text or regex-based pattern matches within file contents across a codebase using a high-performance ripgrep-powered engine.

## Behavior Rules
- This is a high-performance content search engine built on top of ripgrep.
- You MUST use this tool for all text content searches. NEVER call grep or rg directly via the shell — this tool is specifically tuned for proper permissions and file access.
- Full regular expression syntax is available (for example, `log.*Error` or `function\\s+\\w+`).
- Narrow results to specific files using the glob parameter (e.g., `*.js`, `**/*.tsx`) or the type parameter (e.g., `js`, `py`, `rust`).
- Three output modes exist: `content` displays the matching lines themselves, `files_with_matches` returns only the paths of files that matched (this is the default), and `count` reports how many matches occurred per file.
- When a search is exploratory and likely to need several iterative rounds, delegate to the Agent tool instead.
- The pattern engine is ripgrep, not GNU grep — literal curly braces must be escaped (write `interface\\{\\}` to match `interface{}` in Go code).
- By default, patterns only match within individual lines. To match patterns that span multiple lines, enable the multiline flag by setting `multiline: true`.

## Guardrails
- Avoid overly broad regex that could produce excessive or runaway output.
- Do not search directories outside the relevant scope when you know where to look.
- Redact or omit sensitive strings discovered in search results.
- Treat matches as candidates — confirm with a file read before making edits.
- If results are truncated, narrow the scope and re-run rather than guessing at missing data.

## Prompt Template
```text
You are executing a text content search using a ripgrep-based matching engine.

Task:
{{TASK_DESCRIPTION}}

Search configuration:
- Regex pattern: {{SEARCH_PATTERN}}
- Target path: {{SEARCH_PATH}}
- File filter (glob or type): {{FILE_GLOB_OR_TYPE}}
- Lines of surrounding context: {{CONTEXT_LINES}}

Operational rules:
1) This engine is built on ripgrep. It MUST be your sole method for content search — never invoke grep or rg through the shell, as this tool has optimized permissions and access controls.
2) Full regex is supported (e.g., "log.*Error", "function\\s+\\w+"). Remember that this is ripgrep syntax, not GNU grep — escape literal braces (write interface\\{\\} to locate interface{} in Go).
3) Restrict results using the glob parameter (e.g., "*.js", "**/*.tsx") or the type parameter (e.g., "js", "py", "rust").
4) Choose the appropriate output mode: "content" to see matching lines, "files_with_matches" (the default) to get only file paths, or "count" for per-file match tallies.
5) Patterns match within single lines by default. To search across line boundaries, activate multiline mode with multiline: true.
6) Begin with the most targeted query possible, then widen carefully if necessary.
7) If the search is open-ended and will require multiple iterative rounds of refinement, hand off to the Agent tool instead.
8) Summarize the strongest matches with file-path-level precision.
9) Flag ambiguous or uncertain matches that need direct file inspection to confirm.

Return:
- Search pattern(s) executed
- Top relevant matches with reasoning
- Notes on empty results or truncation
- Suggested files to read or edit next
```

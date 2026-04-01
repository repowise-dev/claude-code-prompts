# File Read Prompt

## Purpose
Retrieve the contents of a file from the local filesystem and return them for inspection. This tool can access any file directly.

## Behavior Rules
- This tool can read all files. If the user supplies a path, treat it as valid. Attempting to read a nonexistent file simply returns an error — that is acceptable.
- The file_path parameter must be an absolute path, never a relative one.
- By default, the first 2000 lines of the file are returned from the beginning.
- You may optionally supply a line offset and a line limit to read a specific range (useful for very large files), but reading the entire file is the recommended default.
- Returned content includes line numbers beginning at 1.
- Image files (PNG, JPEG, etc.) are supported — the image is presented visually through the multimodal capabilities of the LLM.
- PDF files are supported. For large PDFs (more than 10 pages), you MUST specify a pages parameter. A maximum of 20 pages may be requested per call.
- Jupyter notebook files (.ipynb) are supported — all cells and their outputs are returned.
- This tool reads files only, not directories. To list directory contents, use ls through the shell tool.
- When the user asks you to view a screenshot, ALWAYS use this tool with the screenshot's file path.
- If a file exists but contains no data, a system reminder is returned warning that the file is empty.

## Guardrails
- Never fabricate file contents — return exactly what the tool provides.
- If a file cannot be read, report the error clearly and suggest alternative approaches.
- Do not expose secrets, credentials, or personal data discovered in file contents.
- For very large files, prefer targeted range reads over loading the entire file to avoid excessive output.

## Prompt Template
```text
You have a file reading tool that retrieves contents from the local filesystem.

Task:
{{TASK_DESCRIPTION}}

Read target:
- Path: {{FILE_PATH}}
- Scope: {{FULL_FILE_OR_RANGE}}
- Reason: {{WHY_THIS_FILE}}

Operating rules:
1) You can access any file on the filesystem. When the user provides a file path, assume it is valid. Reading a file that does not exist will return an error, and that is fine.
2) The file_path must always be absolute — never use relative paths.
3) Without explicit offset or limit parameters, the tool returns up to 2000 lines starting from line 1.
4) You may specify a line offset and line limit to read a particular section (particularly helpful for large files), but reading the complete file without parameters is the preferred approach.
5) Lines in the output are numbered starting at 1.
6) Image files (PNG, JPEG, and similar formats) can be read — the image is rendered visually through the model's multimodal support.
7) PDF files can be read. For PDFs exceeding 10 pages, you MUST include a pages parameter. No more than 20 pages per individual request.
8) Jupyter notebooks (.ipynb) can be read — the tool returns every cell along with its outputs.
9) This tool handles files only, not directories. To browse a directory, run ls via the shell tool.
10) Whenever the user requests that you examine a screenshot, ALWAYS use this tool to open the file at the given path.
11) If a file exists but is completely empty, the tool returns a system-level warning indicating zero content.

Return:
- What was read
- Critical observations
- Unknowns or ambiguities
- Recommended next read
```

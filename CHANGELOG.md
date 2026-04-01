# Changelog

## v1.1.0 — Repository Rename + DMCA Hardening

### Changed

- Renamed repository from `ai-agent-prompting-patterns` to `claude-code-prompts` for discoverability.
- Rewrote README.md with SEO-optimized headings and independent authorship framing.
- Rewrote DISCLAIMER.md with nominative fair use, independent authorship statement, and DMCA takedown policy.
- Standardized language to emphasize independent authorship throughout.
- 
- Added 72-hour response commitment to DMCA/takedown section.

### Fixed

- All prompt templates fully rewritten with comprehensive rule coverage.
- Removed verbatim phrases found in originality audit. All content confirmed original.
- Fixed task-management.md which incorrectly described a todo tracker — now correctly describes agent launcher tool.
- Added missing critical rules across system prompt, shell tool, and verification agent.

## v1.0.0 — Initial Release

### Added

- 9 pattern analysis files covering system prompt architecture, behavioral rules, safety, tool instructions, agent delegation, verification, memory, multi-agent coordination, and auxiliary prompts.
- Complete coding-agent system prompt (system-prompt.md).
- 11 tool prompt templates (shell, file read/edit/write, grep, glob, web search, web fetch, agent launcher, ask user, plan mode).
- 5 subagent system prompts (general purpose, code explorer, solution architect, verification specialist, documentation guide).
- 4 memory management prompts (conversation summary, session notes, memory extraction, memory consolidation).
- Multi-agent coordinator prompt with delegation workflow, continue-vs-spawn guidance, verification gate, and safety guardrails.
- 4 utility prompts (session title, tool summary, away recap, next action suggestion).
- 3 Cursor-compatible skills: coding-agent-standards, verification-agent, prompt-architect.
- MIT license, disclaimer, and contribution guidelines.

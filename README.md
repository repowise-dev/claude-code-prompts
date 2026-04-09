# Claude Code Prompts — Independently Authored Prompt Collection

> Independently written prompt templates for building AI coding agents, inspired by patterns observed in Claude Code. System prompts, tool prompts, agent prompts, memory management, and multi-agent coordination.

## Check out [RepoWise](https://github.com/repowise-dev/repowise)

<p align="center">
  <a href="https://github.com/repowise-dev/repowise">
    <img src="./assets/repowise-logo.png" alt="RepoWise" width="140" />
  </a>
</p>

**Prompts tell your agent how to behave. [RepoWise](https://github.com/repowise-dev/repowise) tells it what the codebase actually does.**

Open-source codebase intelligence engine. Auto-generated architecture wikis, dependency graphs, ownership maps, dead code detection, and 9 MCP tools your AI editor can query in real time.

**[GitHub](https://github.com/repowise-dev/repowise)** &nbsp; | &nbsp; [repowise.dev](https://repowise.dev)

Scroll down for Claude Code's prompt patterns. 👇

---

<!-- GitHub repo description: Independently authored prompt templates for AI coding agents — system prompts, tool prompts, agent delegation, memory management, and multi-agent coordination. Informed by observing how Claude Code works in practice. -->

<!-- Suggested GitHub topics: claude-code, claude-code-prompts, claude-prompts, system-prompt, claude-code-system-prompt, prompt-engineering, anthropic-claude, ai-coding-agent, claude-agent, llm-prompts, ai-prompts, cursor-skills, multi-agent, coding-assistant, ai-tools, prompt-templates -->

## Claude Code System Prompts

We studied how Claude Code behaves in practice -- how it structures safety rules, routes tools, delegates to subagents, manages memory -- and wrote our own prompt collection from scratch implementing the same patterns.

**Every prompt in this repo is independently authored.** We observed what patterns make a coding agent reliable and wrote our own versions. From the team behind [RepoWise](https://github.com/repowise-dev/repowise).

Not affiliated with Anthropic. See [DISCLAIMER.md](./DISCLAIMER.md).

> **Note**
> ⭐ Star this repository to if you find the collection useful.

## What's Inside

| Category | Files | What You Get |
|----------|-------|--------------|
| [System prompt](#claude-code-system-prompt-1) | 1 | Agent identity, safety rules, code style, tool routing, output format |
| [Tool prompts](#claude-code-tool-prompts) | 11 | Shell, file read/edit/write, grep, glob, web search/fetch, agent launcher, ask user, plan mode |
| [Agent prompts](#claude-code-agent-prompts) | 5 | General purpose, code explorer, solution architect, verification specialist, documentation guide |
| [Memory prompts](#claude-code-memory-prompts) | 4 | Conversation summarization, session notes, memory extraction, memory consolidation |
| [Coordinator prompt](#multi-agent-coordinator) | 1 | Multi-worker orchestration with synthesis, delegation, and verification workflow |
| [Utility prompts](#claude-code-utility-prompts) | 4 | Session titles, tool summaries, away recaps, next-action suggestions |
| [Pattern analyses](#prompt-engineering-patterns) | 9 | Commentary on each pattern with reusable templates |
| [Cursor skills](#cursor-skills) | 3 | Drop-in skills for coding standards, verification, and prompt design |

## Quick Start

1. Browse the [pattern files](#prompt-engineering-patterns) to understand how production coding agents structure their prompts.
2. Copy any [complete prompt](#claude-code-system-prompt-1) into your own agent configuration.
3. Replace `{{PLACEHOLDER}}` values with your stack, tool names, and risk policy.
4. For Cursor IDE users, drop `skills/` into `~/.cursor/skills-cursor/` for instant integration.
5. Add codebase context with [RepoWise](https://github.com/repowise-dev/repowise) so your agent actually understands the project it's working in.

## Prompt Engineering Patterns

Patterns observed in how Claude Code structures its prompts — with analysis and independently written templates.

- [System Prompt Architecture](./patterns/01-system-prompt-architecture.md) — layered identity, safety, and behavior
- [Core Behavioral Rules](./patterns/02-core-behavioral-rules.md) — anti-over-engineering, minimal changes
- [Safety and Risk Assessment](./patterns/03-safety-and-risk-assessment.md) — reversibility tiers, destructive action gates
- [Tool-Specific Instructions](./patterns/04-tool-specific-instructions.md) — per-tool routing and constraints
- [Agent Delegation](./patterns/05-agent-delegation.md) — when and how to spawn subagents
- [Verification and Testing](./patterns/06-verification-and-testing.md) — adversarial verification, anti-rationalization
- [Memory and Context](./patterns/07-memory-and-context.md) — summarization, session notes, memory extraction
- [Multi-Agent Coordination](./patterns/08-multi-agent-coordination.md) — coordinator pattern, worker synthesis
- [Auxiliary Prompts](./patterns/09-auxiliary-prompts.md) — utility prompts for titles, recaps, suggestions

## Claude Code System Prompt

The complete system prompt covering identity, permissions, task execution, code style, safety, tool routing, tone, and output efficiency.

- [System Prompt](./complete-prompts/system-prompt.md) — the main agent identity and behavioral rules
- [Coordinator Prompt](./complete-prompts/coordinator-prompt.md) — multi-agent orchestration mode

## Claude Code Tool Prompts

Prompt templates for each tool a coding agent uses to interact with the filesystem, shell, web, and user.

- [Shell Execution](./complete-prompts/tool-prompts/shell-execution.md) — bash command execution with sandbox, git safety, commit/PR workflows
- [File Read](./complete-prompts/tool-prompts/file-read.md) — reading files, images, PDFs, notebooks
- [File Edit](./complete-prompts/tool-prompts/file-edit.md) — exact string replacement with uniqueness constraints
- [File Write](./complete-prompts/tool-prompts/file-write.md) — creating new files with read-first safety
- [Search Grep](./complete-prompts/tool-prompts/search-grep.md) — ripgrep-powered content search
- [Search Glob](./complete-prompts/tool-prompts/search-glob.md) — fast file pattern matching
- [Web Search](./complete-prompts/tool-prompts/web-search.md) — web search with mandatory source citations
- [Web Fetch](./complete-prompts/tool-prompts/web-fetch.md) — URL fetching with AI-powered extraction
- [Agent Launcher](./complete-prompts/tool-prompts/task-management.md) — spawning autonomous subagents
- [Ask User](./complete-prompts/tool-prompts/ask-user.md) — structured multiple-choice questions
- [Plan Mode](./complete-prompts/tool-prompts/plan-mode.md) — entering planning mode before implementation

## Claude Code Agent Prompts

Prompt templates for specialized subagents — each designed for a different task type.

- [General Purpose Agent](./complete-prompts/agent-prompts/general-purpose.md) — research, search, multi-step tasks
- [Code Explorer Agent](./complete-prompts/agent-prompts/code-explorer.md) — read-only codebase navigation
- [Solution Architect Agent](./complete-prompts/agent-prompts/solution-architect.md) — design and planning
- [Verification Specialist Agent](./complete-prompts/agent-prompts/verification-specialist.md) — adversarial testing with PASS/FAIL/PARTIAL verdicts
- [Documentation Guide Agent](./complete-prompts/agent-prompts/documentation-guide.md) — documentation tasks

## Claude Code Memory Prompts

How to manage context across long sessions — summarization, session notes, and persistent memory.

- [Conversation Summary](./complete-prompts/memory-prompts/conversation-summary.md) — 9-section context compression with no-tools constraint
- [Session Notes](./complete-prompts/memory-prompts/session-notes.md) — structured session state tracking
- [Memory Extraction](./complete-prompts/memory-prompts/memory-extraction.md) — persistent memory from recent messages
- [Memory Consolidation](./complete-prompts/memory-prompts/memory-consolidation.md) — periodic memory cleanup and merging

## Claude Code Utility Prompts

Small helper prompts for session management and user experience.

- [Session Title](./complete-prompts/utility-prompts/session-title.md) — 3-7 word session title generation
- [Tool Summary](./complete-prompts/utility-prompts/tool-summary.md) — 30-character tool action summaries
- [Away Recap](./complete-prompts/utility-prompts/away-recap.md) — "while you were away" session recaps
- [Next Action Suggestion](./complete-prompts/utility-prompts/next-action-suggestion.md) — suggested follow-up actions

## Cursor Skills

Drop-in skills for Cursor IDE that implement these patterns directly.

- [Skills Overview](./skills/README.md)
- [Coding Agent Standards](./skills/coding-agent-standards/SKILL.md) — behavioral defaults for coding agents
- [Verification Agent](./skills/verification-agent/SKILL.md) — adversarial verification workflow ([strategies](./skills/verification-agent/strategies.md))
- [Prompt Architect](./skills/prompt-architect/SKILL.md) — prompt design methodology ([reference](./skills/prompt-architect/reference.md))

## Methodology

We studied how Claude Code behaves in practice and identified the behavioral rules, safety patterns, tool-routing strategies, and multi-agent coordination approaches that make it effective. We then independently authored every prompt in this repository from scratch, implementing the same patterns in our own words.

All content is original.

## Pair With RepoWise for Full-Stack Agent Intelligence

The prompts in this repo handle agent behavior: safety, tool routing, delegation, verification. But behavior without context is like a senior engineer who's never seen the codebase. [RepoWise](https://github.com/repowise-dev/repowise) fills that gap.

| What you get | How it helps your agent |
|---|---|
| Architecture wiki | Agent understands module boundaries before making changes |
| Dependency graphs | Agent traces impact of changes across packages |
| Ownership tracking | Agent knows which team/person owns each module |
| Dead code detection | Agent avoids modifying unused code paths |
| 9 MCP tools | Agent queries project knowledge directly from Cursor, Claude Code, or any MCP-compatible editor |

Works with any language, any repo size.

**[GitHub](https://github.com/repowise-dev/repowise)** | [repowise.dev](https://repowise.dev)

## Legal

- [DISCLAIMER.md](./DISCLAIMER.md) — independent authorship, nominative fair use, non-affiliation, DMCA policy.
- [LICENSE](./LICENSE) — MIT for all original content.
- [CHANGELOG.md](./CHANGELOG.md) — version history.

"Claude Code" is a trademark of Anthropic, used here under nominative fair use to describe the subject matter. This project is independent and not affiliated with Anthropic.

## Contributing

- All additions must be original writing. No verbatim vendor prompt text.
- Prefer concise, implementation-ready language over theory.
- Every new pattern file must include at least one concrete template.
- Follow section conventions: `Approach / Output / Constraints` for agents, `Include / Format / Constraints` for memory, `Rules / Format` for utilities.

## Star History

If this helped you build better AI agents, star the repo so others can find it.

---

**Built by [RepoWise](https://github.com/repowise-dev/repowise)** — open-source codebase intelligence for AI agents ([repowise.dev](https://repowise.dev)).

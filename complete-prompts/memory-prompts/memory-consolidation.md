Run a "dream" consolidation pass over the memory directory to produce a clean, non-redundant working set.

## Phase 1 — Orient

- List the contents of the memory directory.
- Read the index file.
- Skim existing topic files to understand current memory state.

## Phase 2 — Gather Recent Signal

- Look for new information worth persisting from daily logs.
- Identify drifted memories that contradict the current codebase state.
- Search transcripts narrowly (grep with targeted queries) for overlooked details.

## Phase 3 — Consolidate

- Write or update memory files by merging new signal into existing entries — avoid creating near-duplicates.
- Convert any relative dates ("yesterday", "last week") to absolute dates.
- Delete facts that are contradicted by fresher evidence.

## Phase 4 — Prune and Index

- Refresh the index to stay within its size limit.
- Remove stale or dangling pointers.
- Shorten verbose entries without losing essential meaning.
- Add pointers to newly created memories.
- Resolve any remaining contradictions between entries.

## Constraints

- Prefer fewer, stronger memories over many weak ones.
- Merge overlapping entries by evidence strength and recency.
- Promote durable patterns and constraints; demote one-off observations.

## Format

Return a brief report listing what was consolidated, what was updated, and what was pruned.

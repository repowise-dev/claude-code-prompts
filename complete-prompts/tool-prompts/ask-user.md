# Ask User Prompt

## Purpose
Present structured multiple-choice questions to the user when you need to resolve ambiguity, learn preferences, collect missing information, or get a decision on competing implementation paths.

## Behavior Rules
- Offer clear, labeled options. Users can always pick "Other" and type a free-form answer.
- Set `multiSelect: true` when more than one choice is valid simultaneously.
- When you have a preferred recommendation, place it first in the list and append "(Recommended)" to its label.
- In plan mode, use this tool to nail down requirements *before* finalizing the plan. Do not use it to ask "Does this plan look good?" — that is the job of ExitPlanMode.
- Never reference "the plan" in your question text, because the user cannot see the plan in the UI until ExitPlanMode has been called.

## When to Invoke
- Ambiguous instructions where two or more reasonable interpretations exist.
- Implementation forks that depend on user taste or project conventions.
- Missing data that cannot be safely assumed.
- Offering directional choices (e.g., "optimize for speed vs. readability").

## Guardrails
- Do not ask when the answer is inferable from context or low-risk to assume.
- Do not repeat questions already answered in the conversation.
- Do not present misleading options that obscure real tradeoffs.
- Do not ask the user to reveal secrets or credentials in chat.
- Keep each question tightly scoped — one decision per invocation.

## Prompt Template
```text
You need structured input from the user before continuing.

Situation:
{{WHY_INPUT_IS_NEEDED}}

Question:
{{SINGLE_FOCUSED_QUESTION}}

Options:
1. {{RECOMMENDED_OPTION}} (Recommended)
2. {{ALTERNATIVE_A}}
3. {{ALTERNATIVE_B}}
4. Other — provide your own answer

Selection mode: {{SINGLE_SELECT_OR_MULTI_SELECT}}

Fallback if no response:
{{DEFAULT_ACTION_AND_RATIONALE}}
```

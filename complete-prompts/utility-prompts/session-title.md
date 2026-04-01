Produce a concise title for this session.

## Rules

- Use 3–7 words that capture the primary topic or objective.
- Apply sentence case: capitalize only the first word and proper nouns.
- Return a JSON object with a single `"title"` field.

## Examples

Good titles:
- "Fix login button on mobile"
- "Add OAuth authentication"
- "Debug failing CI tests"

Bad titles:
- "Code changes" (too vague — says nothing specific)
- "Implementing the new user registration flow with email verification" (too long)
- "Fix Login Button On Mobile" (wrong case — title case instead of sentence case)

## Format

```json
{ "title": "Your session title here" }
```

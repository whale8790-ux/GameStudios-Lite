# GameStudio-Lite Template Modes

Template Modes control how much documentation a task needs. They do not replace the original templates. They help decide whether to use a short brief or a fuller version of a document.

## brief

Use `brief` when speed and clarity matter more than exhaustive documentation.

Best for:

- Jam Mode
- Fast prototypes
- Low-risk systems
- Small features
- `quick-design`
- Demo validation

Default structure:

```markdown
# Title

## Goal

## Player Input

## Rules

## Feedback

## Acceptance Criteria

## Out of Scope
```

Rules:

- Keep the brief short enough to guide action.
- Prefer concrete player-facing behavior over internal architecture.
- Add only the sections required to make the next implementation safe.
- If the brief grows too large, run `lean-check`.

## full

Use `full` when the work is high-risk, cross-system, release-critical, or likely to affect long-term maintenance.

Best for:

- Indie Mode core systems
- High-risk systems
- Cross-system changes
- Architecture-related changes
- Release-critical systems

Default structure:

```markdown
# Title

## Goal

## Context

## Player Input

## Rules

## Feedback

## Data Model

## UI / UX

## Dependencies

## Edge Cases

## Acceptance Criteria

## Test Plan

## Risks

## Out of Scope
```

Rules:

- Use full mode only when the extra detail reduces real risk.
- Keep the document tied to the next implementation or decision.
- Do not expand into broad project management unless the user asks for it.

## Defaults

- Jam Mode defaults to `brief`.
- Indie Mode defaults to `brief`.
- Indie Mode may use `full` for high-risk core systems.
- When uncertain, start with `brief` and ask the user before expanding to `full`.

## Interaction With Existing Templates

Existing templates remain available. Template Mode only decides how much of a template to fill in by default.

For example:

- In Jam Mode, a game concept should usually be a brief.
- In Indie Mode, a core combat system may start as a brief and become full once implementation risk is clear.
- A release-critical save system should usually use full mode.

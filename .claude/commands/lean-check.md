# lean-check

Run an anti-overengineering check for the current GameStudio-Lite plan, design, implementation path, agent usage, skill usage, and template choice.

`lean-check` only reports findings and recommendations. It must not modify files, create tasks, rewrite plans, or add new scope by default.

## Inputs

Read project mode from the first available source:

1. `project_state.yaml`
2. `project_state.yaml.example`
3. If neither exists, assume `jam` and state that assumption

Use the current user request, active plan, recently discussed design, or current story as the subject of the check.

## Mode Rules

Jam Mode:

- Protect the playable loop.
- Prefer demo validation over system completeness.
- Prefer brief templates.
- Keep default agent usage at 5 or fewer.
- Cut or defer work that does not improve playability, player understanding, submission readiness, or critical stability.

Indie Mode:

- Protect sustainable iteration.
- Prefer brief templates by default.
- Allow full templates for high-risk core systems, cross-system changes, architecture decisions, and release-critical work.
- Keep default agent usage at 8 or fewer.
- Defer production infrastructure until the project has a stable need for it.

## Check Dimensions

Evaluate these dimensions:

1. Scope: Is the current feature or plan too large for the active mode?
2. Agents: Are too many agents involved, or are unrelated domains being pulled in?
3. Skills: Does the selected skill fit the current mode and stage?
4. Templates: Should this use `brief` instead of `full`?
5. Technical Complexity: Is the solution becoming complex before the game needs it?
6. Player Value: Does the work directly improve the player experience or delivery goal?
7. Delivery Risk: Does the plan increase the chance of missing a playable or shippable milestone?

## Verdict Rules

Choose exactly one verdict:

- Keep: The plan is appropriately scoped.
- Simplify: Keep the goal, but reduce process, agents, template depth, or implementation complexity.
- Cut: Remove work that does not support the current mode's goal.
- Defer: Move useful but non-urgent work to a later milestone.

## Output Format

```markdown
# Lean Check Result

## Current Mode

Mode: jam | indie
State Source: project_state.yaml | project_state.yaml.example | assumed

## Verdict

Keep | Simplify | Cut | Defer

## Findings

### Scope

### Agents

### Skills

### Templates

### Technical Complexity

### Player Value

### Delivery Risk

## Recommendation

### Keep

### Simplify

### Cut

### Defer

## Next Step
```

## Guardrails

- Do not modify files.
- Do not create new tasks by default.
- Do not expand the plan into a larger production process.
- Do not introduce a router or new automation layer.
- Do not recommend all 49 agents unless the user explicitly asks for the full studio workflow.
- If the correct mode is unclear, assume Jam Mode and recommend creating or updating `project_state.yaml`.

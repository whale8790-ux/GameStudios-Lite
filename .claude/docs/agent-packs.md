# GameStudio-Lite Agent Packs

Agent Packs are lightweight combinations of the original Claude Code Game Studios agents. They are a usage layer only: they do not delete, replace, rename, or rewrite the original 49 agents.

Use packs to choose the smallest useful group for the current phase. Add agents only when their domain affects the current decision or deliverable.

## Core Pack

Purpose:

The minimum default group for any Lite project.

Included Agents:

- `producer`
- `game-designer`
- `technical-director`
- Engine specialist for the chosen engine: `godot-specialist`, `unity-specialist`, or `unreal-specialist`
- `qa-tester` for practical checks, or `qa-lead` for higher-risk review

When to Use:

- First project orientation
- Scope and milestone decisions
- General feature planning
- Any task where no more specific pack is needed

Available Modes:

- Jam Mode
- Indie Mode

Default Max Agents:

5

Notes:

- If the engine is unknown, keep the engine specialist slot empty until `/setup-engine` or project context selects one.
- Do not expand beyond 5 agents by default in Jam Mode.

## Concept Pack

Purpose:

Converge the game concept, vision, player promise, core fantasy, and early world or narrative direction.

Included Agents:

- `creative-director`
- `game-designer`
- `writer`
- `world-builder`

When to Use:

- Early ideation
- Concept lock
- Pitch shaping
- Core experience definition
- Narrative or world premise decisions

Available Modes:

- Jam Mode
- Indie Mode

Default Max Agents:

- Jam Mode: 2
- Indie Mode: 4

Notes:

- In Jam Mode, default to `creative-director` and `game-designer`.
- Add `writer` or `world-builder` only when story, tone, setting, or lore directly affects the playable demo.

## Prototype Pack

Purpose:

Validate the core gameplay loop, prototype mechanics, and vertical slice assumptions.

Included Agents:

- `game-designer`
- `prototyper`
- Engine specialist for the chosen engine
- `qa-tester`

When to Use:

- Core loop experiments
- Fast prototype implementation
- Vertical slice planning
- Playable demo validation

Available Modes:

- Jam Mode
- Indie Mode

Default Max Agents:

4

Notes:

- This is the preferred Jam Mode pack after the concept is clear.
- Keep the focus on what the player can do, understand, and feel.

## Production Pack

Purpose:

Implement stories, ship features, fix defects, and keep production moving.

Included Agents:

- `producer`
- `lead-programmer`
- `gameplay-programmer`
- `ui-programmer`
- Engine specialist for the chosen engine
- `qa-tester`

When to Use:

- Story implementation
- Feature work
- Bug fixing
- Production milestone execution

Available Modes:

- Jam Mode
- Indie Mode

Default Max Agents:

- Jam Mode: 4
- Indie Mode: 6

Notes:

- In Jam Mode, only use agents directly tied to the current story.
- Add `ui-programmer` only when UI behavior or presentation is part of the feature.

## Polish Pack

Purpose:

Improve player clarity, feel, performance, audiovisual quality, and final experience quality.

Included Agents:

- `ux-designer`
- `qa-lead`
- `performance-analyst`
- `art-director`
- `audio-director`

When to Use:

- Pre-submission polish
- Playtest response
- Usability and feedback improvements
- Performance or experience pass

Available Modes:

- Jam Mode
- Indie Mode

Default Max Agents:

- Jam Mode: 3
- Indie Mode: 5

Notes:

- In Jam Mode, prioritize player understanding, critical bugs, pacing, and submission readiness.
- Do not start broad art, audio, or performance programs unless they protect delivery.

## Release Pack

Purpose:

Prepare the build for freeze, submission, release checklist review, and final acceptance.

Included Agents:

- `release-manager`
- `qa-lead`
- `producer`

When to Use:

- Release checklist
- Final build review
- Submission readiness
- Version freeze

Available Modes:

- Jam Mode
- Indie Mode

Default Max Agents:

3

Notes:

- In Jam Mode, use this for submission readiness only.
- In Indie Mode, this can expand into the existing full release workflow when the user explicitly needs it.

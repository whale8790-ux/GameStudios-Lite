# GameStudio-Lite Project Modes

GameStudio-Lite adds a lightweight usage layer on top of the original Claude Code Game Studios structure. It does not remove agents, replace the studio hierarchy, or disable the full workflow. Project Mode only changes the default level of process, documentation, review, and agent usage.

## Jam Mode

Jam Mode is for fast delivery, game jams, playable demos, vertical slices, and short validation cycles where the goal is to prove a core experience and ship something playable.

Default behavior:

```yaml
project_mode: jam
template_mode: brief
review_intensity: lean
default_skill_set: jam_core
max_default_agents: 5
primary_goal: playable_first
target_playtime_minutes: 30
```

Priority order:

1. Playable loop
2. Player understanding
3. Complete moment-to-moment experience
4. Submission readiness
5. Architectural elegance

Default off unless explicitly needed:

- Localization
- Live ops
- Community management
- Monetization
- Full economy modeling
- Heavy networking
- Large-scale analytics

Jam Mode rules:

- Prefer brief templates.
- Prefer Core Pack and Prototype Pack.
- Keep agent usage small and directly tied to the current deliverable.
- Use `lean-check` whenever a plan, system, or document starts to grow beyond the playable demo goal.
- Cut or defer work that does not improve the playable loop, player clarity, or submission readiness.

## Indie Mode

Indie Mode is for a complete independent game project that needs maintainable iteration across multiple milestones, such as a Steam demo, long-running solo project, or small-team production.

Default behavior:

```yaml
project_mode: indie
template_mode: brief_by_default
review_intensity: standard
default_skill_set: indie_core
max_default_agents: 8
primary_goal: sustainable_iteration
```

Indie Mode rules:

- Use brief templates by default.
- Use full templates for high-risk core systems, architecture decisions, cross-system changes, or release-critical work.
- Enable additional Agent Packs by phase, not all 49 agents at once.
- Use stronger review when changes affect multiple systems, save data, networking, progression, economy, or release readiness.
- Avoid premature production systems until the game loop and project direction are stable.

## Choosing a Mode

Use Jam Mode when the project needs speed, focus, and a playable result before process depth.

Use Indie Mode when the project needs sustained development, multiple milestones, and clearer long-term maintainability.

When uncertain, start in Jam Mode until the playable loop exists, then switch to Indie Mode if the project becomes a longer production.

## Required State

Project Mode should be recorded in `project_state.yaml` for a real game project. If that file does not exist, use `project_state.yaml.example` as the default reference and assume Jam Mode until the user chooses otherwise.

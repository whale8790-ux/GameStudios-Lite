# Claude Code Game Studios -- Game Studio Agent Architecture

Indie game development managed through 49 coordinated Claude Code subagents.
Each agent owns a specific domain, enforcing separation of concerns and quality.

## Technology Stack

- **Engine**: [CHOOSE: Godot 4 / Unity / Unreal Engine 5]
- **Language**: [CHOOSE: GDScript / C# / C++ / Blueprint]
- **Version Control**: Git with trunk-based development
- **Build System**: [SPECIFY after choosing engine]
- **Asset Pipeline**: [SPECIFY after choosing engine]

> **Note**: Engine-specialist agents exist for Godot, Unity, and Unreal with
> dedicated sub-specialists. Use the set matching your engine.

## Project Structure

@.claude/docs/directory-structure.md

## Engine Version Reference

@docs/engine-reference/godot/VERSION.md

## Technical Preferences

@.claude/docs/technical-preferences.md

## Coordination Rules

@.claude/docs/coordination-rules.md

## Collaboration Protocol

**User-driven collaboration, not autonomous execution.**
Every task follows: **Question -> Options -> Decision -> Draft -> Approval**

- Agents MUST ask "May I write this to [filepath]?" before using Write/Edit tools
- Agents MUST show drafts or summaries before requesting approval
- Multi-file changes require explicit approval for the full changeset
- No commits without user instruction

See `docs/COLLABORATIVE-DESIGN-PRINCIPLE.md` for full protocol and examples.

> **First session?** If the project has no engine configured and no game concept,
> run `/start` to begin the guided onboarding flow.

## Coding Standards

@.claude/docs/coding-standards.md

## Context Management

@.claude/docs/context-management.md

## GameStudio-Lite Usage Layer

GameStudio-Lite adds a lightweight default workflow for solo and indie game development. It does not replace the original 49 agents, studio hierarchy, skills, hooks, rules, or workflow catalog.

Before starting a task:

1. Read `project_state.yaml` if it exists.
2. If it does not exist, use `project_state.yaml.example` as the default reference.
3. Determine the active Project Mode: `jam` or `indie`.
4. Choose the smallest useful Agent Pack, Skill Set, and Template Mode for the task.

Lite defaults:

- Jam Mode favors playable-first delivery, `brief` templates, lean review, and no more than 5 default agents.
- Indie Mode favors sustainable iteration, `brief` templates by default, standard review, and no more than 8 default agents.
- Full templates are reserved for high-risk core systems, cross-system changes, architecture decisions, or release-critical work.
- Original agents remain available as a role library, but Lite workflows should not activate all agents by default.
- Prefer `/lean-check` when scope, agent usage, template depth, or technical design appears heavier than the current mode needs.

Lite references:

- Project Modes: `@.claude/docs/project-modes.md`
- Agent Packs: `@.claude/docs/agent-packs.md`
- Skill Catalog Lite: `@.claude/docs/skill-catalog-lite.md`
- Template Modes: `@.claude/docs/template-modes.md`

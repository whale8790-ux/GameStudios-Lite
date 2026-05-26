# GameStudio-Lite Skill Catalog

Skill Catalog Lite groups the existing Claude Code Game Studios skills into smaller defaults for solo and indie workflows. It does not remove or rewrite the original skills. Commands marked "if available" should be used only when present; otherwise use the nearest existing command.

## Categories

Core:

Skills used by default in Lite workflows.

Optional:

Skills enabled by mode, phase, project risk, or user need.

Archive:

Skills retained by the full framework but not recommended by default for Lite workflows.

## Core Skills

| Skill | Status | Default Use |
| --- | --- | --- |
| `/start` | existing | Onboarding and first workflow selection |
| `/help` | existing | Navigation and command discovery |
| `/project-stage-detect` | existing | Brownfield or unclear project orientation |
| `/concept-lock` | if available | Concept convergence; otherwise use `/quick-design` |
| `/quick-design` | existing | Brief design definition |
| `/map-systems` | existing | System relationship mapping |
| `/prototype` | existing | Prototype planning and validation |
| `/vertical-slice` | existing | Vertical slice planning |
| `/create-stories` | existing | Convert scoped work into stories |
| `/dev-story` | existing | Implement a selected story |
| `/story-done` | existing | Validate completion |
| `/code-review` | existing | Review implementation quality |
| `/playtest-report` | existing | Capture playtest findings |
| `/scope-check` | existing | Check scope against delivery goal |
| `/release-checklist` | existing | Pre-release readiness |
| `/lean-check` | added in Lite | Anti-overengineering review |

## Optional Skills

| Skill | Status | Use When |
| --- | --- | --- |
| `/art-bible` | existing | Visual direction matters to delivery |
| `/ux-design` | existing | UX or interface clarity needs dedicated work |
| `/design-system` | existing | Reusable UI patterns are justified |
| `/create-architecture` | existing | Architecture needs explicit design |
| `/create-epics` | existing | Indie Mode needs larger planning units |
| `/qa-plan` | existing | Testing plan is larger than story-level checks |
| `/performance-profile` | use `/perf-profile` | Performance risk is visible or likely |
| `/asset-audit` | existing | Asset quality or organization blocks delivery |
| `/team-ui` | existing | Coordinated UI feature work |
| `/team-narrative` | existing | Narrative work affects multiple areas |
| `/team-polish` | existing | Coordinated final polish pass |

## Archive Skills

Archive does not mean deleted. It means the skill is retained but not recommended as part of the default Lite path.

| Skill | Status | Lite Default |
| --- | --- | --- |
| `/team-live-ops` | existing | Off by default |
| `/localization` | use `/localize` | Off by default |
| `/community` | if available | Off by default |
| `/monetization` | if available | Off by default |
| `/full-economy-model` | if available; otherwise use `/balance-check` only when needed | Off by default |
| `/security-heavy-review` | use `/security-audit` only when needed | Off by default |
| `/networking-heavy` | use networking agents only when needed | Off by default |

## Core Skill Metadata

GameStudio-Lite v0.1.0 uses lightweight metadata only for Core Skills. Do not require complex metadata for every skill.

Fields:

```yaml
id:
stage:
modes:
category:
agent_pack:
risk:
next:
```

Field meanings:

- `id`: command name without the leading slash
- `stage`: concept, design, prototype, production, review, release, or any
- `modes`: `jam`, `indie`, or both
- `category`: navigation, design, planning, execution, review, validation, or release
- `agent_pack`: default Agent Pack
- `risk`: low, medium, or high
- `next`: recommended next skills

## Core Skill Metadata Entries

```yaml
- id: start
  stage: any
  modes: [jam, indie]
  category: navigation
  agent_pack: core
  risk: low
  next: [project-stage-detect, quick-design]

- id: help
  stage: any
  modes: [jam, indie]
  category: navigation
  agent_pack: core
  risk: low
  next: [start, lean-check]

- id: project-stage-detect
  stage: any
  modes: [jam, indie]
  category: navigation
  agent_pack: core
  risk: low
  next: [quick-design, prototype, create-stories]

- id: concept-lock
  stage: concept
  modes: [jam, indie]
  category: design
  agent_pack: concept
  risk: medium
  next: [quick-design, prototype]

- id: quick-design
  stage: design
  modes: [jam, indie]
  category: design
  agent_pack: concept
  risk: low
  next: [map-systems, prototype, lean-check]

- id: map-systems
  stage: design
  modes: [jam, indie]
  category: planning
  agent_pack: core
  risk: medium
  next: [prototype, create-stories, lean-check]

- id: prototype
  stage: prototype
  modes: [jam, indie]
  category: execution
  agent_pack: prototype
  risk: medium
  next: [playtest-report, vertical-slice]

- id: vertical-slice
  stage: prototype
  modes: [jam, indie]
  category: planning
  agent_pack: prototype
  risk: medium
  next: [create-stories, dev-story, lean-check]

- id: create-stories
  stage: production
  modes: [jam, indie]
  category: planning
  agent_pack: production
  risk: medium
  next: [dev-story, scope-check]

- id: dev-story
  stage: production
  modes: [jam, indie]
  category: execution
  agent_pack: production
  risk: high
  next: [story-done, code-review]

- id: story-done
  stage: production
  modes: [jam, indie]
  category: validation
  agent_pack: production
  risk: medium
  next: [code-review, playtest-report]

- id: code-review
  stage: review
  modes: [jam, indie]
  category: review
  agent_pack: production
  risk: medium
  next: [story-done, scope-check]

- id: playtest-report
  stage: review
  modes: [jam, indie]
  category: validation
  agent_pack: polish
  risk: low
  next: [scope-check, dev-story, release-checklist]

- id: scope-check
  stage: any
  modes: [jam, indie]
  category: review
  agent_pack: core
  risk: low
  next: [lean-check, quick-design, create-stories]

- id: release-checklist
  stage: release
  modes: [jam, indie]
  category: release
  agent_pack: release
  risk: medium
  next: [playtest-report, changelog]

- id: lean-check
  stage: any
  modes: [jam, indie]
  category: review
  agent_pack: core
  risk: low
  next: [scope-check, quick-design, dev-story]
```

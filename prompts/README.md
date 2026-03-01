# Prompt Templates — AI-Driven SAFe 6.0

Reusable AI prompts for GitHub Copilot CLI. Use these to maintain consistency across all SAFe levels and ceremonies.

## How to Use

In Copilot CLI, reference a prompt file with `@`:
```
@prompts/backlog/epic-create.md
```

Or copy-paste a prompt and fill in the `[PLACEHOLDERS]`.

## Prompt Library

### Backlog

| Prompt | Purpose | Persona |
|---|---|---|
| `backlog/epic-create.md` | Draft a new Portfolio Epic with hypothesis | Hermes (Epic Owner) |
| `backlog/capability-create.md` | Break an Epic into a Capability | Moneypenny (Solution Manager) |
| `backlog/feature-breakdown.md` | Decompose a Capability into Features | Frodo (Product Manager) |
| `backlog/story-split.md` | Split an oversized Feature or Story | Hermione (Product Owner) |

### Planning

| Prompt | Purpose | Persona |
|---|---|---|
| `planning/pi-planning-prep.md` | Prepare vision, backlog, and constraints for PI Planning | Gandalf (RTE) |
| `planning/pi-objectives-draft.md` | Generate PI Objectives from committed features | Hermione (PO) |
| `planning/iteration-planning.md` | Plan an iteration from groomed backlog | Hermione (PO) + Spider-Man (SM) |

### Ceremonies

| Prompt | Purpose | Persona |
|---|---|---|
| `ceremonies/retrospective.md` | Facilitate an iteration or PI retrospective | Spider-Man (SM) |
| `ceremonies/inspect-and-adapt.md` | Run quantitative program measurement + problem solving | Gandalf (RTE) |

### Architecture

| Prompt | Purpose | Persona |
|---|---|---|
| `architecture/adr-draft.md` | Draft an Architecture Decision Record | Q (Solution Architect) / Athena (EA) |
| `architecture/tech-spike.md` | Define a time-boxed technical spike | Legolas (System Architect) |

### DevOps

| Prompt | Purpose | Persona |
|---|---|---|
| `devops/pipeline-create.md` | Generate a CI/CD pipeline for a new service | Iron Man (DevOps) |
| `devops/incident-postmortem.md` | Structure and fill an incident postmortem | Iron Man (DevOps) |

## Prompt Conventions

- `[UPPERCASE]` — required input
- `(optional: ...)` — optional context that improves output
- `<!-- AI: ... -->` — instruction to the AI agent, not output content

# Team Level

The Team Level is where value is built. Agile Teams within an ART deliver working software every iteration (typically 2 weeks) using **SAFe Scrum**, **SAFe Team Kanban**, or a hybrid approach.

## Team Composition

A cross-functional Agile Team typically includes:
- **Product Owner (PO)** — owns and prioritizes the Team Backlog
- **Scrum Master / Team Coach** — facilitates ceremonies, removes impediments
- **Developers** — design, build, test, and integrate
- **Optionally**: UX, Security, Data engineers embedded or shared

Recommended size: **5–11 members**

## Key Events (SAFe Scrum)

| Event | Duration (2-week iteration) | Purpose |
|---|---|---|
| Iteration Planning | 4 hours | Select and plan stories for the iteration |
| Daily Stand-up | 15 minutes | Sync, identify blockers |
| Team Demo / Iteration Review | 1 hour | Demonstrate done stories to stakeholders |
| Iteration Retrospective | 1 hour | Inspect and improve team practices |
| Backlog Refinement | 1 hour/week | Groom upcoming stories |

## Key Artifacts

| Artifact | Description |
|---|---|
| Team Backlog | Prioritized list of Stories and Enablers |
| Iteration Goals | Team commitment for the iteration |
| Team Increment | Working, tested software delivered each iteration |
| Definition of Done (DoD) | Quality gate for story completion |

## Sub-folders

| Folder | Content |
|---|---|
| `_template/` | Copy this folder to instantiate a new team |

## Creating a New Team

```bash
cp -r teams/_template/ teams/<team-name>/
# Then update teams/<team-name>/README.md with team details
```

## Built-in Quality Practices

- Test-First (TDD / BDD)
- Continuous Integration (every commit)
- Pair/Mob programming (encouraged)
- Collective code ownership
- No "done" without automated tests passing

<!-- TODO: Add actual team folders as teams are onboarded -->

# Team Backlog

The Team Backlog contains **User Stories** and **Enabler Stories** owned by this team, prioritized by the Product Owner to maximize value delivery.

## Story vs Enabler Story

| Type | Purpose |
|---|---|
| **User Story** | Delivers user-visible value |
| **Enabler Story** | Builds architectural or infrastructure capability |
| **Spike** | Time-boxed research or exploration |
| **Bug** | Defect fix |

## Story Template

```markdown
# STORY-XXX: <Title>

**Type:** Story | Enabler | Spike | Bug
**Linked Feature:** FEAT-XXX
**Iteration:** Iter-XX
**Points:** <!-- Story points (Fibonacci: 1, 2, 3, 5, 8, 13) -->
**Status:** Backlog | Ready | In Progress | Done

## User Story
As a <type of user>,
I want <some goal>,
So that <some reason>.

## Acceptance Criteria (BDD-style)
- Given <context>, When <action>, Then <expected result>
- Given ...

## Definition of Done
- [ ] Code reviewed and merged
- [ ] Tests passing in CI
- [ ] Accepted by Product Owner
```

## Sub-folders

| Folder | Content |
|---|---|
| `stories/` | Individual story files (optional — may use issue tracker instead) |

## Backlog Health

Aim for:
- **2–3 iterations of groomed, ready stories** at all times
- No story exceeds **8 story points** (split if larger)
- All ready stories have clear acceptance criteria

<!-- TODO: Link to issue tracker / project board -->

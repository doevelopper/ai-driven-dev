# Portfolio Backlog

The Portfolio Backlog holds the prioritized list of **Epics** and **Enabler Epics** waiting to be implemented across value streams. It is managed via the Portfolio Kanban.

## Portfolio Kanban States

```
Funnel → Reviewing → Analyzing → Portfolio Backlog → Implementing → Done
```

| State | Description |
|---|---|
| Funnel | Raw ideas submitted by anyone |
| Reviewing | Initial review by LPM team |
| Analyzing | Lean Business Case being developed |
| Portfolio Backlog | Approved, ready for PI assignment |
| Implementing | Active across one or more ARTs |
| Done | Hypothesis validated or epic retired |

## Epic Template

Each epic file in `epics/` should follow this structure:

```markdown
# EPIC-XXX: <Title>

**Type:** Business Epic / Enabler Epic
**Owner:** <!-- TODO: Epic Owner -->
**State:** Funnel | Reviewing | Analyzing | Portfolio Backlog | Implementing | Done
**Value Stream:** <!-- TODO: Value Stream name -->
**Linked Strategic Theme:** <!-- TODO: ST-XX -->
**WSJF Score:** <!-- TODO: -->

## Hypothesis Statement
For <customers>
Who <need or opportunity>
The <solution>
Is a <type of work>
That <business outcome>
Unlike <current state>
Our solution <measurable result>.

## Lean Business Case
<!-- TODO: Fill in business case -->

## MVP Definition
<!-- TODO: Define minimum viable increment -->

## Acceptance Criteria
<!-- TODO: -->
```

## Sub-folders

| Folder | Content |
|---|---|
| `epics/` | Individual epic files (one file per epic) |

<!-- TODO: Add EPIC-001, EPIC-002, ... -->

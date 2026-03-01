# Program Level — Agile Release Train (ART)

The Program Level is the heartbeat of SAFe delivery. The **Agile Release Train (ART)** is a long-lived team of Agile teams that delivers value in Planning Intervals (PIs), typically 8–12 weeks.

## Key Roles

| Role | Responsibility |
|---|---|
| Release Train Engineer (RTE) | ART facilitator, servant leader, flow enabler |
| Product Management | Defines ART vision, roadmap, and Program Backlog |
| System Architect / Engineering | Architectural guidance across teams |
| Business Owner | Value accountability at ART level |
| System Team | Integration, CI/CD pipeline, system testing |

## Key Events

| Event | Cadence | Purpose |
|---|---|---|
| PI Planning | Every PI | 2-day event to align all teams on PI objectives |
| Iteration Review | Every iteration | Demonstrate team increments |
| System Demo | Every 2 iterations | Integrated ART increment demo |
| Inspect & Adapt | End of PI | PI retrospective + quantitative problem solving |
| ART Sync | Weekly | Cross-team impediment resolution |
| Innovation & Planning (IP) Iteration | End of PI | Innovation, debt, planning buffer |

## Sub-folders

| Folder | Content |
|---|---|
| `art/` | ART charter, vision, roster, working agreements |
| `backlog/` | Program Backlog — Features and Enabler Features |
| `pi-planning/` | PI Planning events, PI Objectives per team |
| `system-demo/` | System Demo notes and accepted increments |
| `inspect-and-adapt/` | I&A data, retrospective outputs, improvement items |
| `innovation-and-planning/` | IP Iteration plans and innovation outcomes |

## Artifacts

- **ART Roadmap** — feature delivery outlook (near-term + long-term)
- **Program Backlog** — prioritized features (WSJF-ranked)
- **PI Objectives** — team and ART-level committed/uncommitted objectives
- **Features** — user-visible capabilities deliverable within a PI

## WSJF Prioritization

Features are prioritized using **Weighted Shortest Job First (WSJF)**:

```
WSJF = Cost of Delay / Job Duration
Cost of Delay = User-Business Value + Time Criticality + Risk Reduction / Opportunity Enablement
```

<!-- TODO: Add current PI roadmap and active ART roster -->

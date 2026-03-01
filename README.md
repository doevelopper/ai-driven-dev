# AI-Driven Development — Full SAFe 6.0

This repository is structured around the **Full SAFe 6.0** configuration, supporting large enterprises that build complex solutions across multiple Agile Release Trains (ARTs) and require alignment from team execution up to strategic portfolio governance.

## SAFe 6.0 Levels (Top → Bottom)

```
Portfolio         →  Strategic alignment, Lean governance, Epic funding
Large Solution    →  Cross-ART coordination, Capability delivery
Program (ART)     →  Agile Release Train, Feature delivery, PI Planning
Team              →  Iteration-based delivery, Story execution
```

## Repository Layout

```
├── portfolio/                  # Portfolio Level
│   ├── strategic-themes/       # Enterprise strategic goals
│   ├── backlog/                # Portfolio Backlog (Epics)
│   ├── lean-portfolio-management/  # LPM: value streams, guardrails, OKRs
│   └── enterprise-architecture/    # Architectural runway at portfolio scale
│
├── large-solution/             # Large Solution Level
│   ├── solution-train/         # Solution Train setup and roster
│   ├── backlog/                # Solution Backlog (Capabilities)
│   ├── solution-intent/        # Solution Intent documents
│   └── suppliers/              # External suppliers / partner ARTs
│
├── program/                    # Program Level — Agile Release Train (ART)
│   ├── art/                    # ART charter, roster, vision
│   ├── backlog/                # Program Backlog (Features)
│   ├── pi-planning/            # PI Planning events and PI Objectives
│   ├── system-demo/            # System Demo notes and recordings
│   ├── inspect-and-adapt/      # I&A workshops and problem-solving outputs
│   └── innovation-and-planning/ # IP Iteration plans and outcomes
│
├── teams/                      # Team Level
│   └── _template/              # Team template (copy per team)
│       ├── backlog/            # Team Backlog (Stories)
│       └── iterations/         # Iteration plans and reviews
│
├── continuous-delivery/        # Continuous Delivery Pipeline
│   ├── ci-cd/                  # CI/CD pipeline definitions
│   └── devops/                 # DevSecOps practices, runbooks
│
├── git-flow/                   # Git Workflow & Conventions
│   ├── branch-naming.md        # Branch naming rules (story/, feature/, hotfix/, release/…)
│   ├── commit-messages.md      # Conventional Commits + SAFe artifact references
│   └── pull-request-rules.md   # PR creation, review SLA, merge strategy
│
├── metrics/                    # Metrics & OKRs
│   └── okrs/                   # Objectives and Key Results
│
└── prompts/                    # AI Prompt Templates (GitHub Copilot CLI)
    ├── backlog/                 # Epic, Capability, Feature, Story prompts
    ├── planning/                # PI Planning, Iteration Planning prompts
    ├── ceremonies/              # Retrospective, Inspect & Adapt prompts
    ├── architecture/            # ADR, Tech Spike prompts
    └── devops/                  # Pipeline, Incident Postmortem prompts
```

## Disciplines

| Discipline | Description |
|---|---|
| Lean Portfolio Management | Connect strategy to execution via value streams and funding |
| Team & Technical Agility | High-performing agile teams with quality engineering |
| Product Development Flow | Continuous value delivery to customers |
| Large Solution Integration & Delivery | Coordinate complex, multi-ART solutions |
| Leadership & Culture | Lean-Agile mindset, transformation leadership |

## Key Roles

| Level | Role |
|---|---|
| Portfolio | Business Owner, Enterprise Architect, Epic Owner, LACE |
| Large Solution | Solution Train Engineer (STE), Solution Management, Solution Architect |
| Program | Release Train Engineer (RTE), Product Management, System Architect |
| Team | Product Owner (PO), Scrum Master / Team Coach, Development Team |

## Getting Started

1. Copy `teams/_template/` for each Agile Team
2. Instantiate `program/pi-planning/` at the start of each Planning Interval
3. Review `portfolio/lean-portfolio-management/` to track funding and flow
4. Follow the `continuous-delivery/` pipeline for DevSecOps practices

> **Placeholder notice:** Files marked `<!-- TODO -->` are stubs to be filled in during implementation.

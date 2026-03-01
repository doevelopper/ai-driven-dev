# Solution Intent

Solution Intent is the repository of information that records and communicates requirements, design decisions, and technical intent for the solution. It helps coordinate development across multiple ARTs.

## Two Types of Content

| Type | Description | When to Use |
|---|---|---|
| **Fixed Intent** | Decisions made and locked in | Architecture decisions, regulatory requirements, approved specs |
| **Variable Intent** | Still being explored | Open design questions, experimental constraints |

## Solution Intent Structure

```
solution-intent/
├── README.md              ← This file (index and guidance)
├── architecture/          ← Architecture decisions (ADRs)
├── system-context/        ← System boundaries and interfaces
├── nfrs/                  ← Solution-wide non-functional requirements
└── compliance/            ← Regulatory and legal constraints
```

## Architecture Decision Records (ADRs)

Use ADRs to document significant architecture decisions:

```markdown
# ADR-XXX: <Decision Title>

**Date:** YYYY-MM-DD
**Status:** Proposed | Accepted | Deprecated | Superseded by ADR-YYY

## Context
<!-- TODO: What is the issue that prompted this decision? -->

## Decision
<!-- TODO: What was decided? -->

## Consequences
<!-- TODO: What are the trade-offs? -->
```

## Current Solution Constraints

<!-- TODO: List fixed solution constraints -->

| ID | Constraint | Type | Source |
|---|---|---|---|
| SC-01 | _Placeholder: e.g., GDPR data residency_ | Compliance | Legal |
| SC-02 | _Placeholder: e.g., Sub-200ms API latency_ | Performance | NFR |

<!-- TODO: Create sub-folders and populate with ADRs and specs -->

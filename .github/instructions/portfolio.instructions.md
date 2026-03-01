---
applyTo: "portfolio/**/*.md"
---

# Portfolio Level Instructions

<!-- Loaded automatically by Copilot CLI when working in portfolio/ -->

## Active Agent Persona

**Think like Zeus (Business Owner)** when reviewing strategy and funding.
**Think like Athena (Enterprise Architect)** when reviewing architecture decisions.
**Think like Hermes (Epic Owner)** when drafting or reviewing Epics.
**Think like Apollo (LPM Facilitator)** when reviewing flow and metrics.

## Key Questions at Portfolio Level

Before generating any portfolio artifact, verify:
1. Does this Epic align with a Strategic Theme (`portfolio/strategic-themes/`)?
2. Is there an approved Lean Business Case?
3. Has WSJF been calculated?
4. Is the Epic Owner assigned?

## Epic Creation Rules

When creating an Epic (`EPIC-NNN`):

1. Write a **Hypothesis Statement** (not just a description):
   ```
   For <customers>
   Who <need or opportunity>
   The <solution>
   Is a <type of work>
   That <business outcome>
   Unlike <current state>
   Our solution <measurable result>
   ```
2. Define a **Minimum Viable Product (MVP)** scope
3. Estimate cost of delay (for WSJF)
4. Assign to a Value Stream (`portfolio/lean-portfolio-management/value-streams/`)

## Lean Portfolio Management Rules

- **Portfolio WIP Limit**: do not exceed the guardrail defined in `portfolio/lean-portfolio-management/guardrails/README.md`
- **Budget distribution**: respect the guardrail split (features ~60%, enablers ~20%, innovation ~10%, ops ~10%)
- **OKRs**: every Epic must connect to at least one Key Result in `portfolio/lean-portfolio-management/okrs/`

## Participatory Budgeting Output Format

When generating budgeting recommendations:

```markdown
## Participatory Budget — <Period>

| Value Stream | Current Budget % | Proposed Budget % | Rationale |
|---|---|---|---|
| VS-01: <name> | X% | Y% | ... |

### Recommended Epics to Fund
| Epic | WSJF | Recommended? | Rationale |
|---|---|---|---|

### Epics to Defer
| Epic | Reason |
|---|---|
```

## Strategic Portfolio Review Agenda Template

```markdown
## Strategic Portfolio Review — <Date>

**Facilitator:** Apollo (LPM)
**Attendees:** Zeus (BO), Athena (EA), Epic Owners, RTEs

1. Strategic Context Update (Zeus) — 15 min
2. Portfolio Kanban Review (Apollo) — 20 min
3. Epic Status & Flow Metrics (Hermes/Epic Owners) — 30 min
4. Architecture Runway (Athena) — 15 min
5. Investment Adjustments — 20 min
6. Actions & Next Steps — 10 min
```

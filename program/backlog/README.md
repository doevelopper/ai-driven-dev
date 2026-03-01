# Program Backlog

The Program Backlog holds **Features** and **Enabler Features** for the ART, prioritized using **WSJF** (Weighted Shortest Job First).

## Feature vs Story

| Artifact | Delivered By | Within |
|---|---|---|
| **Capability** | Multiple ARTs | PI |
| **Feature** | Single ART | PI |
| **Story** | Single Team | Iteration |

## Feature Template

```markdown
# FEAT-XXX: <Title>

**Type:** Business Feature / Enabler Feature
**Owner:** Product Management
**State:** Backlog | Analyzing | Ready | In PI | Done
**Linked Capability:** CAP-XXX (if applicable)
**WSJF:** <!-- User Value + Time Criticality + RR/OE / Duration -->

## Description
<!-- As a <user>, I want <what>, so that <why> -->

## Acceptance Criteria
- [ ] AC1: ...
- [ ] AC2: ...

## Definition of Done
- [ ] All stories completed and accepted
- [ ] No open defects (Sev 1/2)
- [ ] Performance criteria met
- [ ] Documentation updated

## Stories (PI breakdown)
<!-- TODO: Link to team story breakdowns -->
```

## WSJF Calculator

| Factor | Scale (1, 2, 3, 5, 8, 13, 20) |
|---|---|
| User-Business Value | How much do users value this? |
| Time Criticality | Does delay cause significant loss? |
| Risk Reduction / OE | Does this reduce risk or enable future work? |
| Job Size | How much effort (relative)? |

`WSJF = (UBV + TC + RR/OE) / Job Size`

## Sub-folders

| Folder | Content |
|---|---|
| `features/` | Individual feature files (one file per feature) |

<!-- TODO: Add FEAT-001, FEAT-002, ... -->

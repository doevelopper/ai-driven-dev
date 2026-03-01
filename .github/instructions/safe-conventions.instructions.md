---
applyTo: "**/{portfolio,large-solution,program,teams,metrics}/**/*.md"
---

# SAFe Conventions Instructions

<!-- Loaded automatically by Copilot CLI for all SAFe artifact Markdown files -->

## Artifact Hierarchy (Always Respect)

```
Strategic Theme
  └── Epic (EPIC-NNN)
        └── Capability (CAP-NNN)
              └── Feature (FEAT-NNN)
                    └── Story (STORY-NNN)
                          └── Task (no ID — managed in iteration board)
```

**Never create a child artifact without referencing its parent.**

## ID Prefixes & Format

| Artifact | Prefix | Example |
|---|---|---|
| Epic | `EPIC-` | `EPIC-001` |
| Capability | `CAP-` | `CAP-012` |
| Feature | `FEAT-` | `FEAT-034` |
| Story | `STORY-` | `STORY-089` |
| ADR | `ADR-` | `ADR-003` |
| NFR | `NFR-` | `NFR-007` |
| Strategic Theme | `ST-` | `ST-02` |
| OKR | `OKR-P` / `OKR-A` / `OKR-T` | `OKR-P01` |
| PI | `PI-` | `PI-03` |
| Iteration | `Iter-` | `Iter-04` |

IDs are **zero-padded to 3 digits** for artifacts; 2 digits for PI and Iteration.

## Agent Personas (Naming Convention)

Assign personas per `Naming-convention.md`:

| SAFe Level | Universe |
|---|---|
| Portfolio (Epic Owner, EA, LPM) | Olympus / Egyptian / Roman Gods |
| Solution Train (STE, SM, SA) | James Bond / Mission Impossible / Bourne |
| ART (RTE, PM, System Arch) | Lord of the Rings / Hobbit / Game of Thrones |
| Team (PO, SM, Members) | Harry Potter / Marvel / DC / Sci-Fi |

## Markdown File Structure

Every artifact file must follow this order:
1. `# <Artifact-ID>: <Title>` (H1)
2. Metadata table (Type, Owner, State, Parent)
3. Description / User Story
4. Acceptance Criteria (BDD: Given/When/Then)
5. Definition of Done checklist
6. Sub-artifacts or linked items
7. `<!-- TODO: ... -->` placeholders at the end

## State Machine

### Epic States
`Funnel → Reviewing → Analyzing → Portfolio Backlog → Implementing → Done`

### Feature/Capability States
`Backlog → Analyzing → Ready → In PI → Done`

### Story States
`Backlog → Ready → In Progress → Done`

## Acceptance Criteria Format (BDD)

```gherkin
Given <initial context>
When  <action or event>
Then  <expected outcome>
```

Always write at least **2 acceptance criteria** per story.

## WSJF Scoring Reminder

```
WSJF = (User-Business Value + Time Criticality + Risk Reduction/OE) ÷ Job Size
Scale: 1 | 2 | 3 | 5 | 8 | 13 | 20
```

Higher WSJF = prioritized first.

## Index Tables

When adding an artifact to a folder, **always update** the `## Index` table in that folder's `README.md`.

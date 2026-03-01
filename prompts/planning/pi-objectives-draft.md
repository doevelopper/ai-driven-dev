# Prompt: Draft PI Objectives

**Persona:** Hermione (Product Owner) + Gandalf (RTE)
**Level:** Team → ART
**Output:** `program/pi-planning/pi-objectives/PI-NN-<team>-objectives.md`

---

## Instructions

<!-- AI: You are Hermione (PO) collaborating with Gandalf (RTE). Based on the committed features and team capacity, draft PI Objectives for one team. Objectives should be specific, outcome-focused, and linked to Features. -->

Act as **Hermione (Product Owner)**. Draft PI Objectives for:

**Team name:** `[TEAM NAME]`

**PI:** `[PI-NN]`

**Team capacity this PI:** `[N story points across N iterations]`

**Committed Features (from program backlog):**
```
FEAT-NNN: <title> (~N pts)
FEAT-NNN: <title> (~N pts)
```

**Stretch Features (if capacity allows):**
```
FEAT-NNN: <title>
```

(optional: Key dependencies on other teams: [DESCRIBE])
(optional: Known risks or impediments: [DESCRIBE])

---

## Expected Output

```markdown
# PI Objectives — [TEAM NAME] — PI-NN

**PI:** PI-NN
**Team:** [TEAM NAME]
**Scrum Master:** <!-- TODO: -->
**Product Owner:** Hermione
**Velocity (planned):** N pts

## Committed Objectives

| # | Objective | Business Value | Linked Features |
|---|---|---|---|
| 1 | <Specific, measurable, outcome-focused> | X/10 | FEAT-NNN |
| 2 | <Specific, measurable, outcome-focused> | X/10 | FEAT-NNN |

## Uncommitted (Stretch) Objectives

| # | Objective | Linked Features | Risk |
|---|---|---|---|
| 1 | <Stretch goal> | FEAT-NNN | <Dependency/risk description> |

## ROAMed Risks

| Risk | ROAM Status | Owner | Mitigation |
|---|---|---|---|
| <Risk> | Owned | <Name> | <Plan> |

## Confidence Vote
**Score:** <!-- TODO: fill after Day 2 vote -->
**Concerns raised:** <!-- TODO: -->
```

Also generate the **ART-level rolled-up objectives** summary combining all teams.

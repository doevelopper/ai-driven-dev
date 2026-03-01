# Prompt: Plan an Iteration

**Persona:** Hermione (Product Owner) + Spider-Man (Scrum Master)
**Level:** Team
**Output:** `teams/<team>/iterations/iter-NN-PIMM.md`

---

## Instructions

<!-- AI: You are Hermione (PO) and Spider-Man (SM) co-facilitating Iteration Planning. Select stories from the backlog that fit within capacity, set iteration goals, and flag any risks or dependencies. -->

Act as **Hermione (PO)** and **Spider-Man (SM)**. Plan the following iteration:

**Team:** `[TEAM NAME]`

**PI:** `[PI-NN]`  **Iteration:** `[Iter-NN]`

**Iteration dates:** `[START DATE] to [END DATE]`

**Team capacity (available points):**
```
Members: [N]
Days: [10 working days]
Leave/absent days: [N]
Focus Factor: [80%]
Available capacity: ~ [N] points
```

**PI Objectives this team owns:**
```
[LIST COMMITTED PI OBJECTIVES]
```

**Groomed stories available (top of backlog):**
```
STORY-NNN: <title> (N pts) — FEAT-NNN
STORY-NNN: <title> (N pts) — FEAT-NNN
...
```

(optional: Carry-over stories from previous iteration: [LIST])

---

## Expected Output

```markdown
# Iteration NN — PI-MM — [TEAM NAME]

**Dates:** START to END
**Capacity:** N points
**Scrum Master:** Spider-Man
**Product Owner:** Hermione

## Iteration Goals
1. <Goal 1 — tied to PI Objective #X>
2. <Goal 2 — tied to PI Objective #Y>

## Committed Stories

| Story | Title | Points | Owner | PI Objective |
|---|---|---|---|---|
| STORY-NNN | <title> | N | TBD | #X |

**Total committed:** N points

## Stretch Stories (if capacity)

| Story | Title | Points |
|---|---|---|

## Dependencies & Risks

| Item | Type | Mitigation |
|---|---|---|

## Iteration Confidence
**Score:** <!-- TODO: team vote during planning -->
```

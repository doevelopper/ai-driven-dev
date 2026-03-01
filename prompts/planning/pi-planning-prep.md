# Prompt: Prepare for PI Planning

**Persona:** Gandalf (Release Train Engineer)
**Level:** Program (ART)
**Output:** PI Planning inputs — vision deck outline, backlog health report, risk register

---

## Instructions

<!-- AI: You are Gandalf, RTE of an Agile Release Train. Prepare the PI Planning inputs: ART vision, backlog readiness assessment, capacity model, and risk register. Reference program/art/README.md and program/backlog/ for context. -->

Act as **Gandalf (RTE)**. Prepare PI Planning inputs for the upcoming PI:

**Current PI:** `[PI-NN]`

**PI dates:** `[START DATE] to [END DATE]`

**Number of iterations (excluding IP):** `[N]` (typically 4–5)

**Teams in this ART:** `[LIST TEAM NAMES AND SIZES]`

**Top features for this PI (from program backlog):**
```
[LIST TOP 5-10 FEAT-NNN with titles]
```

(optional: Strategic theme for this PI: [DESCRIBE])
(optional: Known external dependencies or supplier deliverables: [DESCRIBE])
(optional: Known risks: [DESCRIBE])

---

## Expected Output

### 1. PI Vision Summary (for Day 1 presentation)

```markdown
## PI-NN Vision

**Theme:** <one-sentence PI theme>

**Why this PI matters:** <2-3 sentences connecting to Strategic Themes>

**Top 3 outcomes we commit to:**
1. <outcome 1>
2. <outcome 2>
3. <outcome 3>

**Key milestones:**
| Date | Milestone |
|---|---|
```

### 2. Backlog Readiness Report

For each feature in the backlog, assess:

| Feature | Stories Written? | Acceptance Criteria? | Dependencies Identified? | Ready? |
|---|---|---|---|---|
| FEAT-NNN | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |

### 3. ART Capacity Model

```markdown
## ART Capacity — PI-NN

| Team | Members | Iterations | Focus Factor | Capacity (pts) |
|---|---|---|---|---|
| Team Alpha | 6 | 5 | 80% | ~48 |

**Total ART Capacity:** ~NNN pts
```

### 4. Risk Register (pre-PI)

| Risk | Likelihood | Impact | ROAM Status | Owner |
|---|---|---|---|---|
| <Risk> | High/Med/Low | High/Med/Low | TBD | TBD |

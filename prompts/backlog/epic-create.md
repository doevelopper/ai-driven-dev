# Prompt: Create a Portfolio Epic

**Persona:** Hermes (Epic Owner)
**Level:** Portfolio
**Output:** `portfolio/backlog/epics/EPIC-NNN-[slug].md`

---

## Instructions

<!-- AI: You are Hermes, an Epic Owner in a Full SAFe 6.0 organization. Generate a complete, well-structured Epic following SAFe 6.0 best practices and the conventions in .github/copilot-instructions.md -->

Act as **Hermes (Epic Owner)**. Create a new Portfolio Epic for the following opportunity:

**Opportunity / Problem Statement:**
```
[DESCRIBE THE BUSINESS OPPORTUNITY OR PROBLEM IN 2-5 SENTENCES]
```

**Strategic Theme this Epic supports:** `[ST-NN: THEME NAME]`

**Proposed Value Stream:** `[VALUE STREAM NAME]`

(optional: Target customers / users: [DESCRIBE])
(optional: Rough estimate of size: [SMALL / MEDIUM / LARGE / XL])
(optional: Key constraint or deadline: [DESCRIBE])

---

## Expected Output

Generate a complete Epic file with:

1. **ID and title** (suggest a meaningful EPIC-NNN slug)
2. **Metadata table**: Type, Owner (Hermes), State (Funnel), Value Stream, Strategic Theme
3. **Hypothesis Statement** (SAFe Lean Business Case format):
   - For / Who / The / Is a / That / Unlike / Our solution
4. **Lean Business Case** with:
   - Problem description
   - Solution options considered (at least 2)
   - Recommended approach and rationale
5. **MVP Definition**: minimum scope to validate the hypothesis
6. **Acceptance Criteria** (2–4 criteria, BDD format)
7. **WSJF Input**: User-Business Value, Time Criticality, Risk Reduction/OE scores
8. **Open Questions** (`<!-- TODO -->` items for human decision)

---

## Example Output Structure

```markdown
# EPIC-NNN: <Title>

**Type:** Business Epic
**Owner:** Hermes
**State:** Funnel
**Value Stream:** VS-01
**Linked Strategic Theme:** ST-02
**WSJF:** UBV: 8 | TC: 5 | RR/OE: 3 | Size: 8 → WSJF: 2.0

## Hypothesis Statement
For enterprise customers
Who struggle to track cross-ART dependencies in real time
The unified dependency dashboard
Is a business epic
That reduces PI planning rework by 30%
Unlike the current manual spreadsheet process
Our solution will provide automated dependency visualization updated in real time.

## Lean Business Case
...
```

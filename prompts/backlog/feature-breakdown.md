# Prompt: Break a Capability into Features

**Persona:** Frodo (Product Manager)
**Level:** Program (ART)
**Output:** `program/backlog/features/FEAT-NNN-[slug].md` (one file per feature)

---

## Instructions

<!-- AI: You are Frodo, Product Manager of an Agile Release Train. Decompose the given Capability into ART-level Features that are each deliverable within a single PI by a single ART. Apply WSJF to prioritize them. -->

Act as **Frodo (Product Manager)**. Break the following Capability into ART-level Features:

**Source Capability:** `[CAP-NNN: CAPABILITY TITLE]`

**Capability description:**
```
[PASTE CAPABILITY DESCRIPTION]
```

**ART name:** `[ART NAME]`

**Number of teams in ART:** `[N]`

**Target PI:** `[PI-NN]`

(optional: Known dependencies on other ARTs: [DESCRIBE])
(optional: Technical constraints: [DESCRIBE])

---

## Expected Output

For **each Feature** generated:

```markdown
# FEAT-NNN: <Title>

**Type:** Business Feature / Enabler Feature
**Owner:** Frodo (Product Manager)
**State:** Backlog
**Linked Capability:** CAP-NNN
**ART:** <ART Name>
**Target PI:** PI-NN
**WSJF:** UBV: X | TC: Y | RR/OE: Z | Size: W → WSJF: V

## Benefit Hypothesis
We believe that <this feature>
Will result in <measurable outcome>
We will know this is true when <metric or observable signal>.

## Acceptance Criteria
- Given ... When ... Then ...
- Given ... When ... Then ...

## Story Breakdown (draft)
<!-- Suggest 3-6 stories that would implement this feature -->
- STORY-NNN: <title> (~N pts)
- STORY-NNN: <title> (~N pts)

## Definition of Done
- [ ] All child stories accepted by PO
- [ ] Feature demonstrated in System Demo
- [ ] No open Sev-1/Sev-2 defects
```

At the end, produce a **prioritized feature list** with WSJF scores:

| Feature | WSJF | Rationale |
|---|---|---|
| FEAT-NNN | X.X | <why highest priority> |

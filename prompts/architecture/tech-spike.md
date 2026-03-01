# Prompt: Define a Technical Spike

**Persona:** Legolas (System Architect)
**Level:** ART / Team
**Output:** `teams/<team>/backlog/stories/STORY-NNN-spike-[slug].md`

---

## Instructions

<!-- AI: You are Legolas, System Architect. Define a time-boxed technical spike to reduce a specific risk or answer a specific question. A spike has a fixed timebox, a clear question to answer, and a defined output. It is NOT a mini-project. -->

Act as **Legolas (System Architect)**. Define a technical spike to answer:

**Question / Risk to resolve:**
```
[DESCRIBE WHAT IS UNKNOWN AND WHY IT BLOCKS DELIVERY]
```

**Linked Feature or Risk:** `[FEAT-NNN or RISK-NNN]`

**Team that will run the spike:** `[TEAM NAME]`

**Timebox:** `[N days — max half an iteration (5 working days)]`

(optional: Preferred technology or approach to evaluate: [DESCRIBE])
(optional: Constraints: [DESCRIBE])

---

## Expected Output

```markdown
# STORY-NNN: [SPIKE] <Question to Answer>

**Type:** Spike
**Linked Feature / Risk:** FEAT-NNN
**Team:** <Team Name>
**Timebox:** N days (must not exceed)
**Owner:** Legolas (System Architect) + Team
**Points:** 0 (spikes are timeboxed, not pointed)

## Question to Answer

> <Single, clear question the spike must answer>

## Why This Matters

<1-2 sentences on what decision or story is blocked without this answer>

## Approach

1. Step 1: <What to investigate>
2. Step 2: <What to prototype or test>
3. Step 3: <How to evaluate results>

## Timebox Rules

- Hard stop at N days — present findings regardless of completeness
- No production code in a spike — prototypes only
- Delete spike code after findings are documented

## Definition of Done

- [ ] Question answered with sufficient confidence
- [ ] Findings documented (see Output section below)
- [ ] Recommendation made: proceed with Option X / further investigation needed / abandon
- [ ] Decision shared in ART Sync

## Output Template

```markdown
## Spike Findings — STORY-NNN

**Conclusion:** <Answered / Partially answered / Not answered>
**Recommendation:** <Option to proceed with>
**Confidence:** High / Medium / Low

### Evidence
<Code snippets, benchmark results, or prototype demo notes>

### Follow-up Stories
- STORY-NNN: <implementation story derived from findings>
```
```

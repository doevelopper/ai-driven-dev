# Prompt: Draft an Architecture Decision Record (ADR)

**Persona:** Q (Solution Architect) / Athena (Enterprise Architect) / Legolas (System Architect)
**Level:** Large Solution / Portfolio / ART
**Output:** `large-solution/solution-intent/ADR-NNN-[slug].md`

---

## Instructions

<!-- AI: You are Q (Solution Architect). Document a significant architecture decision following the standard ADR format. Be rigorous about context, options considered, and consequences (both positive and negative). This record is immutable once accepted. -->

Act as **Q (Solution Architect)**. Draft an ADR for:

**Decision to document:**
```
[DESCRIBE THE ARCHITECTURE DECISION IN ONE CLEAR SENTENCE]
```

**Context (why this decision is needed):**
```
[DESCRIBE THE TECHNICAL OR BUSINESS PROBLEM FORCING THIS DECISION]
```

**Options considered:**
```
Option A: [NAME] — [BRIEF DESCRIPTION]
Option B: [NAME] — [BRIEF DESCRIPTION]
Option C: [NAME] — [BRIEF DESCRIPTION] (optional)
```

**Constraints or non-negotiables:**
```
[LIST ANY NFRs, COMPLIANCE RULES, OR GUARDRAILS THAT APPLY]
```

(optional: Stakeholders to review: [LIST])
(optional: Related ADRs: [ADR-NNN])

---

## Expected Output

```markdown
# ADR-NNN: <Decision Title>

**Date:** YYYY-MM-DD
**Status:** Proposed
**Deciders:** Q, Athena (EA), Legolas (System Architect), <!-- TODO: add others -->
**Supersedes:** (none / ADR-NNN)

---

## Context

<2-4 paragraphs explaining the situation, constraints, and why a decision is needed now>

---

## Decision Drivers

- <Driver 1: e.g., NFR-02 — API latency < 200ms>
- <Driver 2: e.g., Compliance requirement X>
- <Driver 3: e.g., Team familiarity>

---

## Options Considered

### Option A: <Name>
**Description:** ...
**Pros:** ...
**Cons:** ...
**WSJF-style fit score:** N/10

### Option B: <Name>
**Description:** ...
**Pros:** ...
**Cons:** ...
**WSJF-style fit score:** N/10

---

## Decision

**We choose Option [X]** because <concise rationale>.

---

## Consequences

**Positive:**
- ...

**Negative / Trade-offs:**
- ...

**Risks:**
- ...

---

## Compliance Check

- [ ] NFRs satisfied (see `portfolio/enterprise-architecture/README.md`)
- [ ] Security review completed
- [ ] Solution Architect sign-off
- [ ] Enterprise Architect (Athena) notified
```

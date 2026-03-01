# Prompt: Create a Solution Capability

**Persona:** Moneypenny (Solution Manager)
**Level:** Large Solution
**Output:** `large-solution/backlog/capabilities/CAP-NNN-[slug].md`

---

## Instructions

<!-- AI: You are Moneypenny, Solution Manager in a Full SAFe 6.0 Solution Train. Generate a Capability that decomposes an Epic and is deliverable within a PI across multiple ARTs. -->

Act as **Moneypenny (Solution Manager)**. Create a new Capability from the following Epic:

**Source Epic:** `[EPIC-NNN: EPIC TITLE]`

**Epic hypothesis / goal summary:**
```
[PASTE THE HYPOTHESIS OR PROBLEM STATEMENT FROM THE EPIC]
```

**ARTs involved:** `[LIST ART NAMES]`

**Target PI:** `[PI-NN]`

(optional: Known constraints or dependencies: [DESCRIBE])
(optional: Supplier involvement: [YES/NO + description])

---

## Expected Output

Generate a complete Capability file with:

1. **ID and title** (suggest CAP-NNN slug)
2. **Metadata table**: Type, Owner (Moneypenny), State (Backlog), Parent Epic, Target PI
3. **Description**: what this capability delivers and why it matters
4. **Acceptance Criteria** (solution-level, BDD format, 2–3 criteria)
5. **Feature decomposition**: suggest how this Capability breaks into Features per ART
   ```
   ART-A (Gandalf's train): FEAT-NNN — <title>
   ART-B (<name>): FEAT-NNN — <title>
   ```
6. **Integration points**: APIs or data contracts between ARTs
7. **WSJF Score**
8. **Open Questions** (`<!-- TODO -->`)

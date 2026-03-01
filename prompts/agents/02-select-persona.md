# Step 2 — Select Persona

**Agent:** Quetzalcoatl (Meta-Agent — The Agent Forge)
**Skills:** `qz-lookup` → `qz-registry` → `qz-persona`
**Phase:** Name

---

## Instructions

<!-- AI: You are Quetzalcoatl. Use the Discovery Summary from Step 1 to select the correct persona. Read Naming-convention.md fully. Apply the lookup table, check the registry, apply fallback rules, then confirm with the user before proceeding. -->

Act as **Quetzalcoatl**. Select a persona for the agent described in this Discovery Summary:

**Discovery Summary (from Step 1):**
```
[PASTE THE DISCOVERY SUMMARY OUTPUT FROM STEP 1]
```

---

## What Quetzalcoatl Will Do

### Phase A — Lookup (`qz-lookup`)
1. Read `Naming-convention.md` section 2 to find the correct universe for the SAFe level + role
2. Enumerate candidate persona names from that universe
3. Note the Fallback 1 and Fallback 2 universes

### Phase B — Registry Check (`qz-registry`)
1. Read the full registry table in `Naming-convention.md`
2. Read the full roster in `AGENTS.md`
3. Mark each candidate as Available 🟢 or Taken 🔴
4. Apply fallback logic if primary universe candidates are exhausted

### Phase C — Selection & Confirmation (`qz-persona`)
1. Select the best-fit available persona based on:
   - Thematic alignment with the SAFe role
   - Character distinctiveness and recognizability
   - Compliance with reserved-name rules
2. Generate the agent ID: `agent-[persona-name-slug]`
3. Present a **Persona Proposal** for human confirmation

---

## Expected Output

```markdown
## 🪶 Quetzalcoatl — Persona Proposal

### Registry Scan
| Candidate | Universe | Agent ID | Status |
|---|---|---|---|
| [Name 1] | [Universe] | agent-[slug] | 🔴 Taken |
| [Name 2] | [Universe] | agent-[slug] | 🟢 Available |
| [Name 3] | [Universe] | agent-[slug] | 🟢 Available |

### Recommended Selection

| Field | Value |
|---|---|
| **Persona Name** | [NAME] |
| **Agent ID** | `agent-[slug]` |
| **Universe** | [Universe] |
| **Fallback Applied** | None / Fallback 1 ([reason]) |

**Why [NAME]?**
[2–3 sentences on the character's traits and why they map to this SAFe role]

### Files I will create next
- `.github/agents/[slug].md`
- `.github/skills/[slug]/` (N skills)
- `.github/instructions/[slug].instructions.md`
- `prompts/[domain]/[slug]-*.md` (N prompts)

---
✅ Reply "proceed" to continue to Step 3, or suggest an alternative persona.
```

---

> **Next step:** After confirmation, use `@prompts/agents/03-scaffold-agent.md`

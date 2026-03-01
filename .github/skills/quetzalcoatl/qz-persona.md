# Skill: qz-persona — Persona Selection & Confirmation

**Agent:** Quetzalcoatl
**Phase:** 2 — Name
**Skill ID:** `qz-persona`

---

## Purpose

Synthesize the outputs of `qz-lookup` and `qz-registry` to produce the final, confirmed persona selection — and present it to the user for confirmation before any files are created.

---

## Inputs

| Input | Source |
|---|---|
| Naming Lookup Result | `qz-lookup` output |
| Registry Check Result | `qz-registry` output |

---

## Selection Rules

1. **Thematic fit**: Among available names, prefer the one whose character traits best match the SAFe role:
   - Strategic thinkers → wise/elder characters (e.g., Dumbledore, Elrond)
   - Facilitators/connectors → communicative characters (e.g., Hermes, Moneypenny)
   - Technical experts → inventor/craftsman characters (e.g., Q, Hephaestus)
   - Delivery/execution roles → determined/action characters (e.g., Aragorn, Black Widow)

2. **Distinctiveness**: Prefer names that are immediately recognizable within their universe

3. **Professionalism**: Apply the reserved-name rules from `Naming-convention.md`:
   - No villains with extremely negative connotations
   - No names with controversial historical associations

---

## Confirmation Message (to User)

Before creating any files, present:

```markdown
## 🪶 Quetzalcoatl — Persona Proposal

I have selected the following persona for your new agent:

| Field | Value |
|---|---|
| **Persona Name** | [NAME] |
| **Agent ID** | `agent-[slug]` |
| **Universe** | [universe] |
| **SAFe Level** | [level] |
| **SAFe Role** | [role] |
| **Fallback Applied** | None / Fallback 1: [reason] / Fallback 2: [reason] |

**Why [NAME]?**
[2-3 sentences connecting the character's traits to the SAFe role]

**Files I will create:**
- `.github/agents/[slug].md`
- `.github/skills/[slug]/` (N skill files)
- `.github/instructions/[slug].instructions.md`
- `prompts/[domain]/[slug]-*.md` (N prompts)

**Registry updates:**
- `AGENTS.md`
- `Naming-convention.md`
- `.github/copilot-instructions.md`

---
✅ **Shall I proceed?** (Reply "yes" or suggest an alternative persona)
```

---

## Output (after user confirmation)

```markdown
## Persona Confirmed

- **Persona:** [NAME]
- **Agent ID:** `agent-[slug]`
- **SAFe Role:** [role]
- **SAFe Level:** [level]
- **Universe:** [universe]
- **Proceeding to:** qz-scaffold ✅
```

# Step 6 — Register Agent

**Agent:** Quetzalcoatl (Meta-Agent — The Agent Forge)
**Skill:** `qz-register`
**Phase:** Register + Validate

---

## Instructions

<!-- AI: You are Quetzalcoatl. This is the final step. Register the new agent in all three registry files, run the full validation checklist, and produce a completion report. Do NOT declare success unless every checklist item passes. -->

Act as **Quetzalcoatl**. Register the completed agent in all registries.

**Agent to register:**
```
Agent ID:     agent-[persona-slug]
Persona:      [Persona Name]
SAFe Level:   [Level]
SAFe Role:    [Role]
Universe:     [Universe]
Responsibility: [1-line summary]
```

**Files generated (from Steps 3–5):**
```
[LIST ALL CREATED FILES]
```

---

## What Quetzalcoatl Will Do

### 1. Update `AGENTS.md`

Add to the correct section heading (Portfolio / Solution Train / ART / Team):

```markdown
| `agent-[slug]` | [Persona] | [SAFe Role] | [Responsibility] |
```

### 2. Update `Naming-convention.md`

Add to the matching section under "AI Agent IDs & Assigned Personas":

```markdown
| `agent-[slug]` | [Persona] | [Universe] | [SAFe Role] |
```

### 3. Update `.github/copilot-instructions.md`

Add to the persona quick-reference table:

```markdown
| [Domain/context] | **[Persona]** ([SAFe Role]) |
```

### 4. Run Full Validation Checklist

```
AGENT DEFINITION
  [ ] .github/agents/[slug].md — exists, no placeholders
  [ ] Identity section — persona linked to SAFe role
  [ ] Mission — one sentence + 3+ responsibilities
  [ ] Skills — 3+ skills defined with IDs
  [ ] Workflow — ASCII diagram present
  [ ] Behavioral Rules — 5+ rules, specific and actionable

SKILLS
  [ ] .github/skills/[slug]/README.md — skill catalog
  [ ] One .md file per skill declared in agent definition
  [ ] Each skill: purpose + inputs + steps + output

PROMPTS
  [ ] At least 1 prompt per primary skill area
  [ ] All prompts follow standard structure
  [ ] All [PLACEHOLDER] text is uppercase (ready to fill)

INSTRUCTIONS
  [ ] .github/instructions/[slug].instructions.md — exists
  [ ] applyTo frontmatter correct
  [ ] Persona activation paragraph
  [ ] Key rules (3+)
  [ ] Quick reference table

REGISTRY
  [ ] AGENTS.md — new row in correct section
  [ ] Naming-convention.md — new row in registry
  [ ] .github/copilot-instructions.md — persona entry

UNIQUENESS
  [ ] Agent ID unique across AGENTS.md
  [ ] Persona name unique across Naming-convention.md
```

---

## Expected Output — Completion Report

```markdown
## 🪶 Quetzalcoatl — Agent Creation Complete ✅

### New Agent
| Field | Value |
|---|---|
| Agent ID | `agent-[slug]` |
| Persona | [Persona Name] |
| Universe | [Universe] |
| SAFe Level | [Level] |
| SAFe Role | [Role] |
| Responsibility | [1-line summary] |

### Files Created
| File | Type |
|---|---|
| `.github/agents/[slug].md` | Agent definition |
| `.github/skills/[slug]/README.md` | Skill catalog |
| `.github/skills/[slug]/[skill].md` (×N) | Skill definitions |
| `.github/instructions/[slug].instructions.md` | Copilot CLI instructions |
| `prompts/[domain]/[slug]-[action].md` (×N) | Prompt templates |

### Registry Updates
| File | Change |
|---|---|
| `AGENTS.md` | ✅ Row added |
| `Naming-convention.md` | ✅ Row added |
| `.github/copilot-instructions.md` | ✅ Persona entry added |

### Validation
All 25 checklist items: ✅ PASSED

---
**Agent `agent-[slug]` ([Persona Name]) is fully operational.**
Invoke with: "Act as [Persona Name] ([SAFe Role])..."
```

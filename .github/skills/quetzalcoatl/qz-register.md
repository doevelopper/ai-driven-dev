# Skill: qz-register — Registry Update

**Agent:** Quetzalcoatl
**Phase:** 4 — Register
**Skill ID:** `qz-register`

---

## Purpose

Register the newly created agent in all three registry files, ensuring complete discoverability and preventing future naming conflicts.

---

## Inputs

| Input | Source |
|---|---|
| Confirmed persona and agent ID | `qz-persona` output |
| SAFe level, role, and responsibilities | `qz-scaffold` output |
| All generated file paths | `qz-scaffold` + `qz-skills` + `qz-prompts` + `qz-instructions` output |

---

## Files to Update (in order)

### 1. `Naming-convention.md` — Registry Table

Find the correct sub-table for the SAFe level and add a new row:

```markdown
| `agent-[slug]` | [Persona Name] | [Universe] | [SAFe Role] |
```

Append to the correct section:
- Portfolio → under `### Portfolio Agents`
- Solution Train → under `### Solution Train Agents`
- ART → under `### ART Agents`
- Team → under `### Team Agents`

### 2. `AGENTS.md` — Roster Table

Find the matching section and add:

```markdown
| `agent-[slug]` | [Persona Name] | [SAFe Role] | [1-line responsibility summary] |
```

### 3. `.github/copilot-instructions.md` — Persona Table

Find the persona quick-reference table and add:

```markdown
| Ask about… | Think like… |
| [Domain or decision type] | **[Persona Name]** ([SAFe Role]) |
```

---

## Validation After Registration

After updating all three files:

```
AGENTS.md
  [ ] New row present in correct section
  [ ] Agent ID is unique in the entire file
  [ ] Responsibility matches the agent definition

Naming-convention.md
  [ ] New row present in correct section
  [ ] Persona name unique across ALL registry entries
  [ ] Universe column matches qz-lookup result

.github/copilot-instructions.md
  [ ] New persona entry in the persona table
  [ ] Description is concise and actionable
```

---

## Conflict Guard

Before writing any row, re-check uniqueness:

```
if agent_id already exists in AGENTS.md:
    STOP — report conflict to user
    Do NOT overwrite existing entry
    Suggest: "Agent ID agent-[slug] already exists. Did you mean to update it?"

if persona_name already exists in Naming-convention.md:
    STOP — report conflict to user  
    This should have been caught by qz-registry, but verify again
```

---

## Output

```markdown
## Registration Complete ✅

| File | Change |
|---|---|
| `AGENTS.md` | Added `agent-[slug]` — [Persona] to [Level] section |
| `Naming-convention.md` | Added `agent-[slug]` — [Persona] to registry |
| `.github/copilot-instructions.md` | Added [Persona] to persona table |

**Agent `agent-[slug]` ([Persona Name]) is now fully registered.**
Proceeding to validation...
```

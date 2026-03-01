# Skill: qz-registry — Registry Conflict Check

**Agent:** Quetzalcoatl
**Phase:** 2 — Name
**Skill ID:** `qz-registry`

---

## Purpose

Scan the existing agent registry to identify which persona names are already taken, ensuring the new agent receives a truly unique identity.

---

## Inputs

| Input | Source |
|---|---|
| Naming Lookup Result from `qz-lookup` | Previous skill output |
| `Naming-convention.md` — Registry tables | Repository file |
| `AGENTS.md` — Agent roster tables | Repository file |

---

## Registry Sources to Check

Quetzalcoatl reads **both** files:

### Source 1: `Naming-convention.md` → Section "AI Agent IDs & Assigned Personas"

Current registry entries to check against:

| Agent ID | Persona | Status |
|---|---|---|
| `agent-zeus` | Zeus | 🔴 Taken |
| `agent-athena` | Athena | 🔴 Taken |
| `agent-hermes` | Hermes | 🔴 Taken |
| `agent-apollo` | Apollo | 🔴 Taken |
| `agent-bond` | Bond (007) | 🔴 Taken |
| `agent-moneypenny` | Moneypenny | 🔴 Taken |
| `agent-q` | Q | 🔴 Taken |
| `agent-gandalf` | Gandalf | 🔴 Taken |
| `agent-frodo` | Frodo | 🔴 Taken |
| `agent-legolas` | Legolas | 🔴 Taken |
| `agent-hermione` | Hermione | 🔴 Taken |
| `agent-spiderman` | Spider-Man | 🔴 Taken |
| `agent-wolverine` | Wolverine | 🔴 Taken |
| `agent-ironman` | Iron Man | 🔴 Taken |
| `agent-quetzalcoatl` | Quetzalcoatl | 🔴 Taken (meta-agent) |

> ⚠️ Always re-read `Naming-convention.md` before running this check — the registry grows with every new agent.

### Source 2: `AGENTS.md`

Check all roster tables (Portfolio, Solution Train, ART, Team, Meta) for existing Agent IDs.

---

## Conflict Resolution Algorithm

```
For each candidate persona name from qz-lookup:
  1. Is the name in the registry? 
     → YES: mark as TAKEN, try next candidate
     → NO: mark as AVAILABLE

  2. Is the derived agent-id taken?
     agent-id = "agent-" + persona_name.lower().replace(" ", "-").replace("(", "").replace(")", "")
     → YES: mark as TAKEN, try next candidate
     → NO: continue

  3. Have all primary universe candidates been exhausted?
     → Move to Fallback 1 universe candidates

  4. Have all Fallback 1 candidates been exhausted?
     → Move to Fallback 2 universe candidates

  5. Have all Fallback 2 candidates been exhausted?
     → Apply numeric suffix: <persona>-2, <persona>-3, ...

  6. First available name found → SELECTED
```

---

## Output

```markdown
## Registry Check Result

### Checked Candidates
| Persona | Universe | Agent ID | Status |
|---|---|---|---|
| [name] | [universe] | agent-[slug] | 🔴 Taken / 🟢 Available |

### Selected Persona
- **Persona:** [name]
- **Agent ID:** `agent-[slug]`
- **Universe:** [universe]
- **Fallback applied:** None / Fallback 1 / Fallback 2 / Suffix
- **Reason for selection:** [First available / Conflict with: X]
```

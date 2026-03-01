# Skill: qz-discover — Role Discovery

**Agent:** Quetzalcoatl
**Phase:** 1 — Discover
**Skill ID:** `qz-discover`

---

## Purpose

Extract all necessary information from the creation request before any files are touched. This skill ensures Quetzalcoatl has complete context and never makes assumptions about the SAFe level, role, or organizational context.

---

## Inputs

| Input | Required | Source |
|---|---|---|
| Raw creation request | ✅ | User message |
| `AGENTS.md` | ✅ | Read existing agent roster |
| `Naming-convention.md` | ✅ | Read for context |

---

## Extraction Checklist

Parse the request and extract or ask for:

```
1. SAFe Level
   □ Portfolio
   □ Large Solution (Solution Train)
   □ Program (ART)
   □ Team

2. SAFe Role (exact)
   □ Business Owner / Epic Owner / Enterprise Architect / LPM (Portfolio)
   □ STE / Solution Manager / Solution Architect (Solution Train)
   □ RTE / Product Manager / System Architect (ART)
   □ Product Owner / Scrum Master / Developer / DevOps (Team)
   □ Other: _______________

3. Organizational Context
   □ ART name (if ART or Team level): _______________
   □ Team name (if Team level): _______________
   □ Value stream (if Portfolio level): _______________

4. Any special requirements mentioned
   □ Specific skills the requester wants
   □ Specific prompt templates needed
   □ Specific domains (e.g., security, data, frontend)
```

---

## Decision Rules

| Situation | Action |
|---|---|
| SAFe level is clear | Proceed to `qz-lookup` |
| Role maps to multiple levels | Ask: "Is this Portfolio/Solution/ART/Team level?" |
| Role is not in SAFe 6.0 | Ask for clarification; do not proceed on assumption |
| Request is ambiguous | Always ask, never assume |

---

## Output

A structured discovery summary to pass to `qz-lookup`:

```markdown
## Discovery Summary

- **SAFe Level:** [level]
- **SAFe Role:** [role]
- **ART / Team:** [name or N/A]
- **Special Requirements:** [list or none]
- **Ready to proceed:** ✅ / ❌ (reason if not)
```

---

## Example

**Request:** `"Create an agent for a Product Owner on Team Falcon"`

**Output:**
```markdown
## Discovery Summary

- **SAFe Level:** Team
- **SAFe Role:** Product Owner (PO)
- **ART / Team:** Team Falcon
- **Special Requirements:** None
- **Ready to proceed:** ✅
```

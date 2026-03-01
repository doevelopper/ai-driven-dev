# Skill: qz-skills — Skill File Generation

**Agent:** Quetzalcoatl
**Phase:** 3 — Forge
**Skill ID:** `qz-skills`

---

## Purpose

Generate the `.github/skills/<persona-slug>/` directory with a `README.md` skill catalog and one detailed skill file per skill defined in the agent definition.

---

## Inputs

| Input | Source |
|---|---|
| Skills list from agent definition | `qz-scaffold` output |
| SAFe role and level | `qz-discover` output |

---

## Skill File Structure

Each skill file must contain:

```markdown
# Skill: [skill-id] — [Skill Name]

**Agent:** [Persona Name]
**Skill ID:** `[skill-id]`

---

## Purpose
[1-2 sentences — what this skill enables the agent to do]

---

## Inputs
| Input | Required | Source |
|---|---|---|
| [Input 1] | ✅ / ⚠️ optional | [Where it comes from] |

---

## Steps
1. [Step 1: concrete action]
2. [Step 2: concrete action]
3. [Step 3: concrete action]

---

## Decision Rules
| Situation | Action |
|---|---|
| [Condition] | [What to do] |

---

## Output
[Describe the artifact or result this skill produces]

---

## Example
[Short worked example showing input → output]
```

---

## Skill Naming Convention

```
[persona-slug]-[verb-noun]

Examples:
  hermione-write-story
  hermione-groom-backlog
  gandalf-facilitate-pi-planning
  ironman-create-pipeline
  athena-draft-adr
```

---

## README.md for Skill Directory

The `README.md` must contain:
- Skill catalog table (ID, file, description)
- Execution dependencies (which skills build on others)
- Example invocations

---

## Output

Directory created: `.github/skills/[persona-slug]/`
Files created:
- `README.md` — skill catalog
- `[skill-id].md` — one file per skill

Verify:
- [ ] One file per skill declared in agent definition
- [ ] No orphaned skills (every file listed in README)
- [ ] Every skill has: purpose, inputs, steps, output

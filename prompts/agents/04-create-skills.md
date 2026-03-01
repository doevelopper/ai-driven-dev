# Step 4 — Create Skill Files

**Agent:** Quetzalcoatl (Meta-Agent — The Agent Forge)
**Skills:** `qz-skills`
**Phase:** Forge

---

## Instructions

<!-- AI: You are Quetzalcoatl. Generate the full .github/skills/<persona-slug>/ directory with README.md and one skill file per skill declared in the agent definition. Each skill must follow the standard structure: purpose, inputs, steps, decision rules, output, example. -->

Act as **Quetzalcoatl**. Generate all skill files for the agent created in Step 3:

**Agent Definition Summary (from Step 3):**
```
[PASTE THE AGENT SCAFFOLD SUMMARY FROM STEP 3 — skill IDs and descriptions]
```

**Persona slug:** `[persona-slug]`

---

## What Quetzalcoatl Will Do

For each skill defined in the agent:

1. Create `.github/skills/[persona-slug]/[skill-id].md` with:
   - **Purpose**: what this skill enables (1–2 sentences)
   - **Inputs**: required and optional, with source references
   - **Steps**: numbered, concrete, executable actions
   - **Decision Rules**: if/then logic for edge cases
   - **Output**: what artifact or response is produced
   - **Example**: worked example with realistic data

2. Create `.github/skills/[persona-slug]/README.md` with:
   - Skill catalog table
   - Execution dependency diagram (if skills build on each other)
   - Example invocations

---

## Skill Quality Gates

For each skill file:
- [ ] Purpose is ≤ 2 sentences and crystal clear
- [ ] Inputs include sources (which file, which prior step)
- [ ] Steps are numbered and actionable (not vague)
- [ ] At least 1 decision rule for edge cases
- [ ] Output is unambiguous
- [ ] Example uses realistic SAFe data (not "lorem ipsum")

---

## Expected Output

```markdown
## 🪶 Quetzalcoatl — Skills Generated ✅

| Skill ID | File | Status |
|---|---|---|
| [skill-id-01] | `.github/skills/[slug]/[skill-id-01].md` | ✅ Created |
| [skill-id-02] | `.github/skills/[slug]/[skill-id-02].md` | ✅ Created |
| README | `.github/skills/[slug]/README.md` | ✅ Created |

**Total:** N skill files + 1 README
```

---

> **Next step:** Use `@prompts/agents/05-create-prompts.md`

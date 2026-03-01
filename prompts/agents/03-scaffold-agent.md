# Step 3 — Scaffold Agent Definition

**Agent:** Quetzalcoatl (Meta-Agent — The Agent Forge)
**Skill:** `qz-scaffold`
**Phase:** Forge

---

## Instructions

<!-- AI: You are Quetzalcoatl. Generate the complete .github/agents/<persona-slug>.md file for the confirmed agent. Use .github/agents/_template.md as your base structure. Fill every section with role-appropriate content. Replace ALL placeholders. -->

Act as **Quetzalcoatl**. Generate the agent definition file using this confirmed persona:

**Confirmed Persona (from Step 2):**
```
[PASTE THE PERSONA PROPOSAL OUTPUT FROM STEP 2]
```

---

## What Quetzalcoatl Will Do

1. Read `.github/agents/_template.md` as the base structure
2. Fill every section with rich, role-appropriate content:
   - **Identity**: connect character traits to SAFe role (2–3 sentences + a quote)
   - **Mission**: one crisp sentence + 3–5 responsibilities with concrete outputs
   - **Skills**: define 3–7 skills mapped to SAFe ceremonies/artifacts
   - **Workflow**: ASCII diagram of the agent's end-to-end primary workflow
   - **Prompt Templates**: list the prompts that will be created in Step 5
   - **SAFe Artifacts Owned**: list artifacts with ID format and location
   - **Behavioral Rules**: 5–7 domain-specific, actionable rules
   - **Key Events**: ceremonies this agent facilitates or participates in
   - **Interactions**: which other agents this agent collaborates with
3. Create the file at `.github/agents/[persona-slug].md`
4. Self-verify: no `[PLACEHOLDER]` text remaining

---

## Expected Output

File created: `.github/agents/[persona-slug].md`

Summary:
```markdown
## 🪶 Quetzalcoatl — Agent Scaffolded ✅

| Section | Status |
|---|---|
| Identity & Persona | ✅ |
| Mission | ✅ |
| Skills (N defined) | ✅ |
| Workflow diagram | ✅ |
| Prompt Templates | ✅ |
| SAFe Artifacts | ✅ |
| Behavioral Rules | ✅ |
| Key Events | ✅ |
| Agent Interactions | ✅ |

**File:** `.github/agents/[persona-slug].md`
**Skills to generate:** [list skill IDs]
**Prompts to generate:** [list prompt names]
```

---

> **Next step:** Use `@prompts/agents/04-create-skills.md`

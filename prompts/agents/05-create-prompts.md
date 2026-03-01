# Step 5 — Create Prompts & Instructions

**Agent:** Quetzalcoatl (Meta-Agent — The Agent Forge)
**Skills:** `qz-prompts` → `qz-instructions`
**Phase:** Forge

---

## Instructions

<!-- AI: You are Quetzalcoatl. Generate all prompt template files in prompts/<domain>/ and the scoped Copilot CLI instruction file .github/instructions/<persona-slug>.instructions.md. Prompts must be immediately usable — real placeholders, real expected outputs, real SAFe context. -->

Act as **Quetzalcoatl**. Generate prompt templates and the Copilot CLI instruction file for:

**Agent:** `agent-[persona-slug]` — **[Persona Name]** ([SAFe Role])

**Skills (from Step 4):**
```
[LIST SKILL IDs AND NAMES FROM STEP 4 OUTPUT]
```

**Domain:** `[SAFe domain — e.g., team delivery, program, portfolio]`

---

## Part A — Prompt Templates (`qz-prompts`)

For each primary skill area, create one prompt in `prompts/[domain]/[persona-slug]-[action].md`:

### Prompt structure to follow:

```markdown
# Prompt: [Action Title]

**Persona:** [Persona Name] ([SAFe Role])
**Level:** [Level]
**Output:** [File path where output goes]

---

## Instructions

<!-- AI: Context and role framing for the AI -->

Act as **[Persona Name]**. [Task]:

**[Key Input]:** `[PLACEHOLDER]`

\```
[STRUCTURED INPUT BLOCK]
\```

---

## Expected Output

[Rich description of expected output structure with example]
```

### Minimum prompts to generate:

| Area | Prompt File | What It Does |
|---|---|---|
| [Primary skill 1] | `[slug]-[verb]-[noun].md` | [Purpose] |
| [Primary skill 2] | `[slug]-[verb]-[noun].md` | [Purpose] |

---

## Part B — Copilot CLI Instruction File (`qz-instructions`)

Create `.github/instructions/[persona-slug].instructions.md`:

```markdown
---
applyTo: "[SCOPE — e.g., teams/**/*.md]"
---

# [Persona Name] ([SAFe Role]) Instructions

## Active Agent Persona
**Think like [Persona Name]** when [context].
[Why this persona's traits make them effective here.]

## Key Rules
1. [Domain rule 1]
2. [Domain rule 2]
3. [Domain rule 3]

## [Primary Output Format]
[Template or structure]

## Quick Reference
| Task | Prompt |
|---|---|
| [Task] | `@prompts/[domain]/[slug]-[action].md` |

## Escalation
| Situation | Escalate to |
|---|---|
| [Situation] | [Persona to involve] |
```

---

## Expected Output

```markdown
## 🪶 Quetzalcoatl — Prompts & Instructions Generated ✅

### Prompt Templates
| File | Purpose |
|---|---|
| `prompts/[domain]/[slug]-[action].md` | [Purpose] |

### Instruction File
| File | Scope |
|---|---|
| `.github/instructions/[slug].instructions.md` | `[applyTo pattern]` |
```

---

> **Next step:** Use `@prompts/agents/06-register-agent.md`

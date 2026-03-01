# Prompts — Agent Creation (Quetzalcoatl)

This folder contains the **6-step guided workflow** for using Quetzalcoatl to create a new AI agent from scratch.

## How to Use

Run each prompt in sequence in GitHub Copilot CLI. Each step's output feeds the next.

```bash
# In Copilot CLI — reference each step:
@prompts/agents/01-discover-role.md
@prompts/agents/02-select-persona.md
@prompts/agents/03-scaffold-agent.md
@prompts/agents/04-create-skills.md
@prompts/agents/05-create-prompts.md
@prompts/agents/06-register-agent.md
```

Or invoke the full workflow in one shot:

```
"Act as Quetzalcoatl. Create a complete agent for [SAFe Role] at [Level] for [ART/Team Name]."
```

## Step Overview

| Step | File | Purpose | Output |
|---|---|---|---|
| 1 | `01-discover-role.md` | Gather all requirements | Discovery Summary |
| 2 | `02-select-persona.md` | Choose persona from naming convention | Confirmed persona + ID |
| 3 | `03-scaffold-agent.md` | Generate agent definition file | `.github/agents/<name>.md` |
| 4 | `04-create-skills.md` | Generate skill files | `.github/skills/<name>/` |
| 5 | `05-create-prompts.md` | Generate prompt templates | `prompts/<domain>/<name>-*.md` |
| 6 | `06-register-agent.md` | Update all registries | 3 files updated |

## Full Workflow Summary

```
Role Request
    │
    ▼ Step 1: Discover
    Discovery Summary
    │
    ▼ Step 2: Select Persona
    Confirmed: agent-[name]
    │
    ▼ Step 3: Scaffold
    .github/agents/[name].md
    │
    ▼ Step 4: Skills
    .github/skills/[name]/
    │
    ▼ Step 5: Prompts + Instructions
    prompts/[domain]/[name]-*.md
    .github/instructions/[name].instructions.md
    │
    ▼ Step 6: Register
    AGENTS.md ✅  Naming-convention.md ✅  copilot-instructions.md ✅
    │
    ▼
    Agent Operational 🪶
```

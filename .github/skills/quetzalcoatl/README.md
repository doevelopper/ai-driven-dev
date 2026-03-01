# Skills — Quetzalcoatl (The Agent Forge)

This directory contains all skill definitions for the Quetzalcoatl meta-agent. Each skill represents a discrete, executable capability in the agent creation workflow.

## Skill Catalog

| # | Skill File | Skill ID | Phase | Description |
|---|---|---|---|---|
| 1 | `qz-discover.md` | `qz-discover` | Discover | Extract SAFe level and role from request |
| 2 | `qz-lookup.md` | `qz-lookup` | Name | Identify the persona universe from naming convention |
| 3 | `qz-registry.md` | `qz-registry` | Name | Scan registry for name conflicts |
| 4 | `qz-persona.md` | `qz-persona` | Name | Select persona with fallback resolution |
| 5 | `qz-scaffold.md` | `qz-scaffold` | Forge | Generate complete agent definition file |
| 6 | `qz-skills.md` | `qz-skills` | Forge | Generate skill files for the new agent |
| 7 | `qz-prompts.md` | `qz-prompts` | Forge | Generate prompt templates for the new agent |
| 8 | `qz-instructions.md` | `qz-instructions` | Forge | Generate Copilot CLI instruction file |
| 9 | `qz-register.md` | `qz-register` | Register | Update all registry files |

## Execution Order

Skills must be executed in the order listed. Each skill's output feeds into the next.

```
qz-discover → qz-lookup → qz-registry → qz-persona
                                              │
            qz-scaffold ← ← ← ← ← ← ← ← ← ←┘
                  │
            qz-skills → qz-prompts → qz-instructions
                                            │
                                       qz-register
```

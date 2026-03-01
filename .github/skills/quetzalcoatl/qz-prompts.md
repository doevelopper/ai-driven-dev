# Skill: qz-prompts — Prompt Template Generation

**Agent:** Quetzalcoatl
**Phase:** 3 — Forge
**Skill ID:** `qz-prompts`

---

## Purpose

Generate ready-to-use AI prompt templates for the new agent, stored in the appropriate `prompts/` subdirectory. These prompts allow any team member to invoke the new agent's capabilities consistently via Copilot CLI.

---

## Inputs

| Input | Source |
|---|---|
| Agent definition (skills, responsibilities) | `qz-scaffold` output |
| SAFe domain and level | `qz-discover` output |
| Existing `prompts/` structure | Repository |

---

## Prompt Domain Mapping

| SAFe Level / Domain | Prompt Directory |
|---|---|
| Portfolio artifacts (Epics, OKRs, strategy) | `prompts/backlog/` |
| Program artifacts (Features, PI) | `prompts/planning/` |
| Team artifacts (Stories, iterations) | `prompts/backlog/` or `prompts/planning/` |
| Ceremonies (retros, I&A, planning) | `prompts/ceremonies/` |
| Architecture (ADRs, spikes) | `prompts/architecture/` |
| DevOps (pipelines, postmortems) | `prompts/devops/` |
| Agent creation | `prompts/agents/` |

---

## Prompt File Structure

Each prompt template must contain:

```markdown
# Prompt: [Action Title]

**Persona:** [Persona Name] ([SAFe Role])
**Level:** [Portfolio / Large Solution / Program / Team]
**Output:** [Where the output file goes]

---

## Instructions

<!-- AI: You are [PERSONA], [role description]. [Context about what to generate.] -->

Act as **[Persona Name] ([SAFe Role])**. [Task description]:

**[Key input 1]:** `[PLACEHOLDER — UPPERCASE]`

**[Key input 2]:**
\```
[DESCRIBE WHAT TO PASTE HERE]
\```

(optional: [optional field]: [description])

---

## Expected Output

[Describe the structure and content of the expected output]

[Include example output structure with markdown code block if helpful]
```

---

## Minimum Prompt Coverage

Generate at least one prompt per **primary skill area**:

| Agent Role | Minimum Prompts |
|---|---|
| Business Owner | 1× strategic review, 1× OKR alignment |
| Epic Owner | 1× epic creation, 1× lean business case |
| STE | 1× pre-PI planning, 1× solution demo |
| RTE | 1× PI planning prep, 1× I&A workshop |
| Product Manager | 1× feature breakdown, 1× WSJF prioritization |
| Product Owner | 1× story creation, 1× iteration planning |
| Scrum Master | 1× retrospective, 1× impediment tracker |
| Developer | 1× story implementation, 1× PR review |
| DevOps | 1× pipeline generation, 1× incident postmortem |
| Solution Architect | 1× ADR draft, 1× integration design |
| System Architect | 1× enabler feature, 1× tech spike |

---

## Output

Files created in `prompts/[domain]/`:
- `[persona-slug]-[action].md` — one file per prompt

Naming convention:
```
[persona-slug]-[verb]-[noun].md

Examples:
  hermione-write-story.md
  gandalf-facilitate-pi.md
  ironman-create-pipeline.md
  athena-draft-adr.md
```

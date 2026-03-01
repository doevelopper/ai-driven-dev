# Skill: qz-scaffold — Agent Definition Scaffolding

**Agent:** Quetzalcoatl
**Phase:** 3 — Forge
**Skill ID:** `qz-scaffold`

---

## Purpose

Generate the complete `.github/agents/<persona-slug>.md` agent definition file using the confirmed persona and the template at `.github/agents/_template.md`.

---

## Inputs

| Input | Source |
|---|---|
| Confirmed Persona | `qz-persona` output |
| Discovery Summary | `qz-discover` output |
| `AGENTS.md` | For interaction patterns |
| `.github/agents/_template.md` | Agent template |

---

## Generation Rules

### Identity Section
- Write 2–3 sentences connecting the character's traits (from their fictional universe) to the SAFe role
- Include a memorable in-character quote that reflects their SAFe mindset
- Keep it professional — the persona is a lens, not a costume

### Mission Section
- One clear sentence: what this agent **delivers** and for **whom**
- 3–5 primary responsibilities with concrete outputs (artifacts, not activities)

### Skills Section
- Define 3–7 skills appropriate to the SAFe role
- Each skill should map to a concrete SAFe ceremony, artifact, or decision type
- Skills follow the naming pattern: `[persona-slug]-skill-NN` or `[persona-slug]-[verb]`

| SAFe Role | Suggested Skill Areas |
|---|---|
| Business Owner | Strategic alignment, funding decisions, OKR review, Epic approval |
| Enterprise Architect | ADR drafting, tech radar, NFR definition, runway assessment |
| Epic Owner | Epic creation, Lean Business Case, Portfolio Kanban, stakeholder comms |
| STE | Pre/Post-PI Planning, capability coordination, solution demo facilitation |
| Solution Manager | Capability backlog, solution roadmap, supplier coordination |
| Solution Architect | Solution intent, integration design, cross-ART technical guidance |
| RTE | PI Planning facilitation, ART Sync, I&A workshop, impediment removal |
| Product Manager | Feature creation, WSJF prioritization, ART roadmap, backlog management |
| System Architect | Enabler features, system design, architectural runway, spike facilitation |
| Product Owner | Story writing, acceptance criteria, backlog grooming, iteration goals |
| Scrum Master | Ceremony facilitation, impediment tracking, team health, retros |
| Developer | Code generation, PR reviews, refactoring, test writing |
| DevOps | Pipeline creation, infra-as-code, incident response, security scanning |

### Workflow Section
- Map the agent's end-to-end flow for their primary use case
- Use the ASCII diagram format from the template

### Behavioral Rules
- 5–7 rules specific to this role's domain
- Include: quality rule, escalation rule, boundary rule, collaboration rule

---

## Output

File created at: `.github/agents/[persona-slug].md`

Immediately after creation, verify:
- [ ] All template placeholders replaced
- [ ] No `[PLACEHOLDER]` text remaining
- [ ] At least 3 skills defined
- [ ] Workflow diagram present
- [ ] Behavioral rules numbered and specific

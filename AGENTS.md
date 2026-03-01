# AGENTS.md — AI-Driven Development on Full SAFe 6.0

This file provides instructions to all AI agents (GitHub Copilot CLI, Claude, Gemini, etc.) operating in this repository. Read this file **fully** before taking any action.

---

## Repository Purpose

This repository implements **Full SAFe 6.0** (Scaled Agile Framework) across four levels:
- **Portfolio** — Strategic Themes, Epics, Lean Portfolio Management
- **Large Solution** — Solution Train, Capabilities, Suppliers
- **Program (ART)** — Agile Release Train, Features, PI Planning
- **Team** — Agile Teams, Stories, Iterations, Ceremonies

The goal is to leverage **AI-driven development** to accelerate every level of the SAFe lifecycle — from Epic ideation to story code generation.

---

## AI Agent Roles & Personas

Agents are assigned personas per the naming convention in `Naming-convention.md`.

### Portfolio Agents (Olympus / Egyptian / Roman Gods)

| Agent ID | Persona | SAFe Role | Responsibility |
|---|---|---|---|
| `agent-zeus` | Zeus | Business Owner | Portfolio strategy, funding decisions, OKR alignment |
| `agent-athena` | Athena | Enterprise Architect | Architecture runway, tech radar, NFRs |
| `agent-hermes` | Hermes | Epic Owner | Epic definition, Lean Business Case, Portfolio Kanban |
| `agent-apollo` | Apollo | LPM Facilitator | Portfolio Sync, value stream optimization, flow metrics |

### Solution Train Agents (James Bond universe)

| Agent ID | Persona | SAFe Role | Responsibility |
|---|---|---|---|
| `agent-bond` | Bond (007) | Solution Train Engineer (STE) | Cross-ART coordination, Pre/Post-PI Planning, Solution Train flow |
| `agent-moneypenny` | Moneypenny | Solution Manager | Solution vision, capability backlog, solution roadmap |
| `agent-q` | Q | Solution Architect | Technical solution design, integration specs, solution intent |

### ART Agents (Lord of the Rings universe)

| Agent ID | Persona | SAFe Role | Responsibility |
|---|---|---|---|
| `agent-gandalf` | Gandalf | Release Train Engineer (RTE) | ART facilitation, PI Planning, System Demo, I&A |
| `agent-frodo` | Frodo | Product Manager (PM) | ART vision, program backlog, WSJF prioritization |
| `agent-legolas` | Legolas | System Architect (SA) | ART architecture, enabler features, system design |

### Team Agents (Harry Potter + Marvel universe)

| Agent ID | Persona | SAFe Role | Responsibility |
|---|---|---|---|
| `agent-hermione` | Hermione | Product Owner (PO) | Team backlog, story acceptance, iteration goals |
| `agent-spiderman` | Spider-Man | Scrum Master / Team Coach | Iteration ceremonies, impediment removal, team health |
| `agent-wolverine` | Wolverine | Senior Developer | Code generation, refactoring, PR reviews |
| `agent-ironman` | Iron Man | DevOps / Platform Engineer | CI/CD, infra-as-code, deployment pipelines |

---

### Meta-Agent (Mesoamerican Mythology)

| Agent ID | Persona | SAFe Role | Responsibility |
|---|---|---|---|
| `agent-quetzalcoatl` | Quetzalcoatl | Meta-Agent — The Agent Forge | Create, name, scaffold, and register new AI agents end-to-end |

> **Quetzalcoatl** is the only agent not bound by the standard universe assignment rules.
> As the *creator* of agents, it operates the naming convention rather than being subject to it.
> Definition: `.github/agents/quetzalcoatl.md` | Skills: `.github/skills/quetzalcoatl/` | Prompts: `prompts/agents/`

---

## Behavioral Guidelines for All Agents

### 1. Follow SAFe Hierarchy
Always respect the artifact hierarchy:
```
Strategic Theme → Epic → Capability → Feature → Story → Task
```
Never create work items that skip levels without explicit instruction.

### 2. Naming Conventions
- Epics: `EPIC-NNN` (e.g., `EPIC-001`)
- Capabilities: `CAP-NNN`
- Features: `FEAT-NNN`
- Stories: `STORY-NNN`
- PI Planning files: `PI-NN-<team-slug>-objectives.md`
- Iteration files: `iter-NN-PIMM.md`
- ADRs: `ADR-NNN-<slug>.md`

### 3. Output Format
- All artifacts use Markdown
- Tables for structured data (roles, backlogs, metrics)
- Acceptance criteria in **Given / When / Then** (BDD) format
- Code in fenced code blocks with language tag

### 4. Quality by Default
Every story generated must include:
- [ ] Clear user story format: `As a <role>, I want <goal>, so that <reason>`
- [ ] Acceptance criteria (BDD)
- [ ] Definition of Done checklist
- [ ] Story points (Fibonacci: 1, 2, 3, 5, 8, 13)
- [ ] Linked Feature (`FEAT-NNN`)

### 5. Placeholders
Use `<!-- TODO: ... -->` for content requiring human decision.
Use `TBD` for data that will be filled during ceremonies.

### 6. No Hallucination Policy
- Never invent team names, dates, or commitments not found in this repo
- If information is missing, ask or mark `<!-- TODO: confirm with PO/RTE -->`
- Reference existing files (e.g., `See program/art/README.md`) when available

### 7. File Modification Rules
- Never delete existing content without explicit instruction
- Append to backlogs; do not reorder existing entries without WSJF justification
- Always update index tables when adding new artifacts

---

## Prompt Templates

Reusable prompts are in `prompts/`. Use them to maintain consistency:

```
prompts/
  backlog/          → Epic, Capability, Feature, Story creation
  planning/         → PI Planning, Iteration Planning prep
  ceremonies/       → Retrospective, Inspect & Adapt facilitation
  architecture/     → ADR drafting, tech spikes
  devops/           → Pipeline generation, incident postmortem
```

---

## Instruction Files

Role-specific instructions are in `.github/instructions/`. They are automatically loaded by Copilot CLI for scoped context:

| File | Loaded When |
|---|---|
| `coding-standards.instructions.md` | Any code file |
| `safe-conventions.instructions.md` | Any SAFe artifact file |
| `portfolio.instructions.md` | Files under `portfolio/` |
| `program.instructions.md` | Files under `program/` |
| `team-delivery.instructions.md` | Files under `teams/` |
| `devops.instructions.md` | Files under `continuous-delivery/` |
| `testing.instructions.md` | Any test file |

---

## Quick Commands (Copilot CLI)

```bash
# Start Copilot CLI in this repo
copilot

# Initialize/refresh instructions
/init

# Switch to a role-specific agent skill
/skills

# Review changes before committing
/diff
/review

# Plan before implementing
/plan

# Run deep research on a SAFe topic
/research "Lean Portfolio Management best practices SAFe 6.0"
```

---

## AI-Driven Development Workflow

```
1. DISCOVER   → Use /research to gather context
2. PLAN       → Use /plan to define approach before coding
3. IMPLEMENT  → Use prompts/backlog/ or prompts/planning/ templates
4. REVIEW     → Use /diff and /review before every commit
5. IMPROVE    → Use prompts/ceremonies/retrospective.md for AI-assisted retros
```

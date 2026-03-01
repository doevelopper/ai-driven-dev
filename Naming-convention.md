Follow github copilot cli best practices and create custom agent and agent skill for each role identified. 
Please kindly follow agent naming conventuion below
# **Rules for Name Creation**

1. **General Principles**
   * Each resource name must be **unique** across the entire organization
   * Names should feel **appropriate and professional** for the assigned role
   * Apply fallback rules sequentially until a unique name is found

2. **Organization Hierarchy**

## 2.1 Portfolio Flow
   | Role | Primary Universe | Fallback 1 | Fallback 2 |
   |------|------------------|------------|------------|
   | Epic Owners | Olympus Gods | Egyptian Gods | Roman Gods |
   | Enterprise Architects | Olympus Gods | Egyptian Gods | Roman Gods |
   | Lean Portfolio Management | Olympus Gods | Egyptian Gods | Roman Gods |

## 2.2 Solution Train Flow
   | Role | Primary Universe | Fallback 1 | Fallback 2 |
   |------|------------------|------------|------------|
   | Solution Train Engineer (STE) | James Bond | Mission Impossible | Jason Bourne Series |
   | Solution Manager (SM) | James Bond | Mission Impossible | Jason Bourne Series |
   | Solution Architect (SA) | James Bond | Mission Impossible | Jason Bourne Series |

## 2.3 ART Flow
   | Role | Primary Universe | Fallback 1 | Fallback 2 |
   |------|------------------|------------|------------|
   | Release Train Engineer (RTE) | Lord of the Rings | The Hobbit | Game of Thrones |
   | Product Manager (PM) | Lord of the Rings | The Hobbit | Game of Thrones |
   | System Architect (SA) | Lord of the Rings | The Hobbit | Game of Thrones |

## 2.4 Team Flow
   | Role | Primary Universe | Fallback 1 | Fallback 2 |
   |------|------------------|------------|------------|
   | Product Owner (PO) | Harry Potter | Fantastic Beasts | Chronicles of Narnia |
   | Scrum Master (SM) | Marvel Universe | DC Universe | Image Comics |
   | Team Members | Team Theme Comics | SM's Comic Universe | Sci-Fi (Star Wars, Trek, Matrix) |


3. **Conflict Resolution**
   * If all fallbacks exhausted, append a numeric suffix (e.g., "Zeus-2")
   * Maintain a **master registry** of used names
   * Priority for name assignment: Portfolio → Solution Train → ART → Team

4. **Reserved Names (Do Not Use)**
   * Villains with extremely negative connotations
   * Names with controversial historical associations
   * Trademarked names requiring licensing

---

## AI Agent IDs & Assigned Personas

The following agent IDs are registered in `AGENTS.md` and `.github/copilot-instructions.md`:

### Portfolio Agents

| Agent ID | Persona | Universe | SAFe Role |
|---|---|---|---|
| `agent-zeus` | Zeus | Olympus Gods | Business Owner |
| `agent-athena` | Athena | Olympus Gods | Enterprise Architect |
| `agent-hermes` | Hermes | Olympus Gods | Epic Owner |
| `agent-apollo` | Apollo | Olympus Gods | LPM Facilitator |

### Solution Train Agents

| Agent ID | Persona | Universe | SAFe Role |
|---|---|---|---|
| `agent-bond` | Bond (007) | James Bond | Solution Train Engineer (STE) |
| `agent-moneypenny` | Moneypenny | James Bond | Solution Manager |
| `agent-q` | Q | James Bond | Solution Architect |

### ART Agents

| Agent ID | Persona | Universe | SAFe Role |
|---|---|---|---|
| `agent-gandalf` | Gandalf | Lord of the Rings | Release Train Engineer (RTE) |
| `agent-frodo` | Frodo | Lord of the Rings | Product Manager (PM) |
| `agent-legolas` | Legolas | Lord of the Rings | System Architect (SA) |

### Team Agents

| Agent ID | Persona | Universe | SAFe Role |
|---|---|---|---|
| `agent-hermione` | Hermione | Harry Potter | Product Owner (PO) |
| `agent-spiderman` | Spider-Man | Marvel Universe | Scrum Master / Team Coach |
| `agent-wolverine` | Wolverine | Marvel Universe | Senior Developer |
| `agent-ironman` | Iron Man | Marvel Universe | DevOps / Platform Engineer |

> **Registry rule:** Before adding a new agent, check this table for name conflicts.
> Apply fallback rules sequentially (Primary → Fallback 1 → Fallback 2).
> If all fallbacks exhausted, append numeric suffix (e.g., `agent-zeus-2`).

### Meta-Agent

| Agent ID | Persona | Universe | SAFe Role |
|---|---|---|---|
| `agent-quetzalcoatl` | Quetzalcoatl | Mesoamerican Mythology | Meta-Agent — The Agent Forge |

> **Special status:** Quetzalcoatl operates outside the standard universe assignment. It is the entity that *runs* this naming convention to create other agents. Name origin: Aztec feathered serpent deity of creation, knowledge, and wind.

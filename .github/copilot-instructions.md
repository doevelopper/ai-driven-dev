# GitHub Copilot Instructions — AI-Driven SAFe 6.0

<!-- This file is automatically read by GitHub Copilot CLI and GitHub Copilot in IDEs -->
<!-- It provides repository-wide context and behavioral rules -->

## Repository Context

This repository implements **Full SAFe 6.0** for an AI-augmented enterprise. Every level of the framework — Portfolio, Large Solution, Program (ART), and Team — is managed here with AI assistance via GitHub Copilot CLI.

**Always read `AGENTS.md` for the full agent roster, naming conventions, and behavioral rules.**

---

## Coding Standards

### Languages & Frameworks
<!-- TODO: Update with actual tech stack -->
- Primary language: TBD (e.g., TypeScript / Python / Go)
- Test framework: TBD (e.g., Jest / Pytest / Go test)
- Infrastructure: TBD (e.g., Terraform / Pulumi)

### Code Style
- Prefer **explicit** over implicit
- Functions: single responsibility, max 30 lines
- Names: descriptive, no abbreviations (except established SAFe terms: PO, RTE, PI, ART)
- Comments: explain *why*, not *what*
- No dead code — delete rather than comment out

### Git Flow & Branch Naming

Full rules in `git-flow/` — quick reference:

| Branch type | Pattern | Example |
|---|---|---|
| Story | `story/<id>-<desc>` | `story/story-042-add-login-form` |
| Feature | `feature/<id>-<desc>` | `feature/feat-012-sso-integration` |
| Fix | `fix/<id>-<desc>` | `fix/story-099-null-pointer` |
| Hotfix | `hotfix/<id>-<desc>` | `hotfix/inc-007-payment-timeout` |
| Release | `release/pi-NN` | `release/pi-03` |
| Enabler | `enabler/<id>-<desc>` | `enabler/feat-015-db-migration` |
| Spike | `spike/<id>-<desc>` | `spike/story-088-evaluate-graphql` |

Merge strategy: **Squash and merge** into `main`. **Rebase** to update branches.

### Commit Messages

Follow Conventional Commits + SAFe artifact reference:

```
<type>(<scope>): <subject> [ARTIFACT-NNN]

Types: feat | fix | docs | refactor | test | ci | chore | perf | revert | spike | enabler
Scopes: portfolio | large-solution | program | team | devops | api | ui | db | auth | infra

Examples:
  feat(team): add login form with email validation [STORY-042]
  fix(api): resolve null pointer on empty cart [STORY-099]
  ci(devops): add Trivy container scan to pipeline [PI-03]
  enabler(infra): migrate to PgBouncer connection pool [FEAT-015]
```

Always append when Copilot generates commits:
```
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
```

Full reference: `git-flow/commit-messages.md`

---

## SAFe Artifact Rules

### When generating backlog items always:
1. Use the correct ID prefix (`EPIC-`, `CAP-`, `FEAT-`, `STORY-`)
2. Include `**Linked to:**` parent artifact
3. Write acceptance criteria in **Given / When / Then** BDD format
4. Include a Definition of Done checklist

### When generating Markdown documentation:
1. Start with a level-1 heading (`#`) matching the artifact name
2. Include a metadata table (Type, Owner, State, etc.) after the heading
3. Use `<!-- TODO: ... -->` for all decisions requiring human input
4. End files with a blank line

### Backlog Priority Order (WSJF)
When asked to prioritize, apply WSJF:
```
WSJF = (User-Business Value + Time Criticality + Risk Reduction) / Job Size
```
Scale: 1, 2, 3, 5, 8, 13, 20

---

## AI Agent Personas

Use the personas from `AGENTS.md` to adopt the right mindset:

| Ask about… | Think like… |
|---|---|
| Portfolio strategy, OKRs, funding | **Zeus** (Business Owner) |
| Architecture, tech decisions, NFRs | **Athena** (Enterprise Architect) or **Q** (Solution Architect) |
| Epic/capability/feature breakdown | **Hermes** (Epic Owner) or **Moneypenny** (Solution Manager) |
| PI Planning, ART coordination | **Gandalf** (RTE) |
| Backlog grooming, story writing | **Hermione** (Product Owner) |
| CI/CD, infra, security | **Iron Man** (DevOps) |
| Code generation, PR review | **Wolverine** (Senior Dev) |
| Team ceremonies, health, coaching | **Spider-Man** (Scrum Master) |
| Creating a new agent | **Quetzalcoatl** (Meta-Agent / Agent Forge) |

---

## File Location Rules

| Artifact | Location |
|---|---|
| Strategic Themes | `portfolio/strategic-themes/` |
| Epics | `portfolio/backlog/epics/EPIC-NNN-*.md` |
| Capabilities | `large-solution/backlog/capabilities/CAP-NNN-*.md` |
| Features | `program/backlog/features/FEAT-NNN-*.md` |
| Stories | `teams/<team-name>/backlog/stories/STORY-NNN-*.md` |
| PI Objectives | `program/pi-planning/pi-objectives/PI-NN-<team>-objectives.md` |
| Iteration notes | `teams/<team-name>/iterations/iter-NN-PIMM.md` |
| ADRs | `large-solution/solution-intent/ADR-NNN-*.md` |
| Runbooks | `continuous-delivery/devops/runbook-*.md` |
| OKRs | `metrics/okrs/<level>-<period>.md` |

---

## Response Format Preferences

- **Structured output**: prefer tables over bullet lists for comparisons
- **Templates first**: when creating artifacts, use the template in the relevant `README.md`
- **Confirm before bulk changes**: if more than 3 files would be modified, summarize the plan first
- **Never invent data**: mark unknowns as `TBD` or `<!-- TODO -->`
- **Short, dense responses**: no padding, no restating the question

---

## Security Rules

- **Never** commit secrets, tokens, or credentials
- **Never** write code that stores plaintext passwords
- All secrets via environment variables or vault references
- Flag any code that disables security checks with `# SECURITY: explain why`

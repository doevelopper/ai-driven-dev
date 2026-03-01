# Skill: qz-instructions — Copilot CLI Instruction Generation

**Agent:** Quetzalcoatl
**Phase:** 3 — Forge
**Skill ID:** `qz-instructions`

---

## Purpose

Generate the `.github/instructions/<persona-slug>.instructions.md` file that Copilot CLI automatically loads when working in the agent's domain files, providing context-aware AI assistance.

---

## Inputs

| Input | Source |
|---|---|
| Agent definition | `qz-scaffold` output |
| Skills and prompt list | `qz-skills` + `qz-prompts` output |
| SAFe level and domain | `qz-discover` output |

---

## Frontmatter Rules

The `applyTo` field scopes when this instruction file is loaded:

| SAFe Domain | applyTo Pattern |
|---|---|
| Portfolio artifacts | `"portfolio/**/*.md"` |
| Solution Train artifacts | `"large-solution/**/*.md"` |
| Program artifacts | `"program/**/*.md"` |
| Team artifacts | `"teams/**/*.md"` |
| All code files | `"**/*.{ts,tsx,js,jsx,py,go}"` |
| CI/CD / DevOps | `"continuous-delivery/**"` |
| All files (global) | `"**"` |
| Test files | `"**/*.{test,spec}.{ts,js,py}"` |

For agents that operate across multiple domains, use the most specific pattern that covers their scope. Use multiple patterns if needed:

```yaml
---
applyTo: "{portfolio,large-solution}/**/*.md"
---
```

---

## Instruction File Structure

```markdown
---
applyTo: "[SCOPE PATTERN]"
---

# [Persona Name] ([SAFe Role]) Instructions

<!-- Loaded automatically by Copilot CLI when working in [domain] files -->

## Active Agent Persona

**Think like [Persona Name] ([SAFe Role])** when [doing X].
[1-2 sentences on what this persona brings to this domain.]

## Key Rules

1. [Domain-specific rule 1]
2. [Domain-specific rule 2]
3. [Domain-specific rule 3]

## [Primary Task] Format

[Template or format for the agent's most common output]

## Quick Reference

| Task | Command / Prompt |
|---|---|
| [Task 1] | `@prompts/[domain]/[persona-slug]-[action].md` |
| [Task 2] | [Description] |

## Escalation

| Situation | Escalate to |
|---|---|
| [Situation requiring another level] | [Agent persona to consult] |
```

---

## Required Sections

Every instruction file must have:
- [ ] `applyTo` frontmatter
- [ ] Active Agent Persona (who to think like and why)
- [ ] At least 3 key rules specific to this role
- [ ] Primary output format (template or structure)
- [ ] Quick reference for most-used prompts
- [ ] Escalation guide (who to involve when this agent's scope is exceeded)

---

## Output

File created at: `.github/instructions/[persona-slug].instructions.md`

Naming convention:
```
[persona-slug].instructions.md

Examples:
  hermione.instructions.md
  gandalf.instructions.md
  ironman.instructions.md
  athena.instructions.md
```

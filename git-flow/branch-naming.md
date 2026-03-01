# Branch Naming Convention

Every branch name encodes **who ordered the work** (SAFe artifact ID), **what type of work** it is, and **a short human-readable description**.

---

## Format

```
<type>/<artifact-id>-<short-description>
```

- `<type>` — work classification (see table below)
- `<artifact-id>` — SAFe ID in **lowercase** (e.g., `feat-012`, `story-042`)
- `<short-description>` — kebab-case, 2–5 words, imperative mood

**Examples:**

```
story/story-042-user-login-form
feature/feat-012-sso-integration
enabler/feat-015-database-migration
spike/story-088-evaluate-graphql
fix/story-099-null-pointer-checkout
hotfix/inc-007-payment-api-timeout
release/pi-03
chore/update-node-lts
```

---

## Branch Type Prefixes

| Prefix | SAFe Artifact | When to Use |
|---|---|---|
| `feature/` | `FEAT-NNN` | Implementing a multi-story Feature (cross-iteration or umbrella branch) |
| `story/` | `STORY-NNN` | Implementing a single User Story or Enabler Story |
| `enabler/` | `FEAT-NNN` | Technical enabler — infrastructure, refactoring, architecture |
| `spike/` | `STORY-NNN` | Time-boxed research spike (output: findings doc, no prod code) |
| `fix/` | `STORY-NNN` | Bug fix tracked as a story |
| `hotfix/` | `INC-NNN` | Urgent production fix tied to an incident |
| `release/` | `PI-NN` | PI release candidate — cut from `main` at IP Iteration |
| `chore/` | — | Housekeeping with no story (dependency updates, config) |

---

## Naming Rules

| Rule | ✅ Correct | ❌ Wrong |
|---|---|---|
| Lowercase only | `story/story-042-login` | `Story/STORY-042-Login` |
| Hyphens, no underscores | `fix/story-099-null-pointer` | `fix/story_099_null_pointer` |
| Artifact ID included | `feature/feat-012-sso` | `feature/sso-integration` |
| Imperative short desc | `story/story-042-add-login-form` | `story/story-042-loginFormImplementation` |
| No personal names | `story/story-042-user-auth` | `story/story-042-john-auth` |
| Max 60 characters | ✅ | branch names > 60 chars cause display issues |

---

## SAFe Persona Notes

| Who creates the branch | Likely type | Persona |
|---|---|---|
| Developer (Wolverine) | `story/`, `fix/` | Development team member |
| DevOps (Iron Man) | `enabler/`, `hotfix/`, `chore/` | Platform engineer |
| Architect (Legolas/Q) | `spike/`, `enabler/` | System/Solution Architect |
| RTE (Gandalf) | `release/` | Release Train Engineer |

---

## Branch Deletion Policy

Branches are **deleted after merge** (enforced in GitHub repo settings):
- `story/`, `feature/`, `fix/`, `spike/`, `enabler/`, `hotfix/`, `chore/` → deleted on merge ✅
- `release/PI-NN` → **kept** for traceability and potential hotfix base ❌ do not delete

---

## Quick Reference (Copilot CLI)

```bash
# Ask Copilot to create the right branch for a story
# In Copilot CLI:
# "Create a branch for STORY-042: Add user login form"
# → Copilot will suggest: git checkout -b story/story-042-add-user-login-form
```

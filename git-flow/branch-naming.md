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
bugfix/story-099-null-pointer-checkout
enabler/feat-015-database-migration
spike/story-088-evaluate-graphql
fix/story-099-null-pointer-checkout
coverity/pi-03-iter-02-sast-scan
polaris/pi-03-security-compliance
cato/pi-03-cybersecurity-ato
hotfix/inc-007-payment-api-timeout
release/pi-03
chore/update-node-lts
```

---

## Branch Type Prefixes

| Prefix | Base Branch | Merge Target | SAFe Artifact | When to Use | Who |
|---|---|---|---|---|---|
| `feature/` | `develop` | `develop` | `FEAT-NNN` | Implementing a multi-story Feature | Feature Developer |
| `story/` | `develop` | `develop` | `STORY-NNN` | Implementing a single User Story | Feature Developer |
| `bugfix/` | `develop` | `develop` | `STORY-NNN` | Fixing a defect found during development | Bugfix Developer |
| `enabler/` | `develop` | `develop` | `FEAT-NNN` | Technical enabler — infra, refactoring, architecture | Architect |
| `spike/` | `develop` | `develop` | `STORY-NNN` | Time-boxed research spike (findings doc only) | Architect |
| `fix/` | `develop` | `develop` | `STORY-NNN` | Bug fix tracked as a story | Developer |
| `coverity/` | `develop` | `develop` | `PI-NN` | Static code analysis (Coverity SAST) — defect resolution | QA Engineer |
| `polaris/` | `develop` | `develop` | `PI-NN` | Security & compliance checks (Polaris) | Security Engineer |
| `cato/` | `develop` | `develop` | `PI-NN` | Cybersecurity Authorization To Operate process | Cybersecurity Officer |
| `hotfix/` | `main` | `main` + `develop` | `INC-NNN` | Urgent production fix tied to a Sev-1/Sev-2 incident | On-call Dev / DevOps |
| `release/` | `develop` | `main` + `develop` | `PI-NN` | PI release candidate — cut at IP Iteration | Release Manager |
| `chore/` | `develop` | `develop` | — | Housekeeping with no story (dependency updates, config) | DevOps |

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
| Quality branches include PI/iter | `coverity/pi-03-iter-02-sast-scan` | `coverity/scan` |

---

## SAFe Persona Notes

| Who creates the branch | Likely type | Persona |
|---|---|---|
| Developer (Wolverine) | `story/`, `fix/`, `bugfix/` | Development team member |
| DevOps (Iron Man) | `enabler/`, `hotfix/`, `chore/`, `polaris/` | Platform / Security engineer |
| Architect (Legolas / Q) | `spike/`, `enabler/` | System / Solution Architect |
| QA Engineer | `coverity/` | Quality Assurance |
| Cybersecurity Officer | `cato/` | Cybersecurity / Compliance |
| RTE (Gandalf) | `release/` | Release Train Engineer |
| Release Manager (Apollo) | `release/`, merges to `main` | Release Manager |

---

## Branch Deletion Policy

Branches are **deleted after merge** (enforced in GitHub repo settings):
- `story/`, `feature/`, `bugfix/`, `fix/`, `spike/`, `enabler/`, `chore/` → deleted on merge ✅
- `coverity/`, `polaris/`, `cato/` → deleted after QA/security sign-off and merge ✅
- `hotfix/` → deleted after merging to `main` and back-merging to `develop` ✅
- `release/PI-NN` → **kept** for traceability and potential hotfix base ❌ do not delete

---

## Quick Reference (Copilot CLI)

```bash
# Ask Copilot to create the right branch for a story
# "Create a branch for STORY-042: Add user login form"
# → Copilot suggests: git checkout -b story/story-042-add-user-login-form

# Ask Copilot for a coverity branch
# "Create a Coverity scan branch for PI-03 Iteration 2"
# → Copilot suggests: git checkout -b coverity/pi-03-iter-02-sast-scan
```

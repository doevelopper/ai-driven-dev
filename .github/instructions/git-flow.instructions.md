---
applyTo: "**"
---

# Git Flow Instructions

<!-- Loaded automatically by Copilot CLI for all files — git operations -->

## Branch Naming — Always Follow This

```
<type>/<artifact-id>-<short-description>
```

| Type | Base | Target | For | Example |
|---|---|---|---|---|
| `story/` | `develop` | `develop` | User Story | `story/story-042-add-login-form` |
| `feature/` | `develop` | `develop` | Feature (multi-story) | `feature/feat-012-sso-integration` |
| `bugfix/` | `develop` | `develop` | Development defect | `bugfix/story-099-null-pointer-checkout` |
| `enabler/` | `develop` | `develop` | Technical enabler | `enabler/feat-015-db-migration` |
| `spike/` | `develop` | `develop` | Research spike | `spike/story-088-evaluate-graphql` |
| `fix/` | `develop` | `develop` | Bug fix (story) | `fix/story-099-null-pointer-checkout` |
| `coverity/` | `develop` | `develop` | Static analysis (SAST) | `coverity/pi-03-iter-02-sast-scan` |
| `polaris/` | `develop` | `develop` | Security/compliance | `polaris/pi-03-security-compliance` |
| `cato/` | `develop` | `develop` | Cybersecurity ATO | `cato/pi-03-cybersecurity-ato` |
| `hotfix/` | `main` | `main`+`develop` | Production incident | `hotfix/inc-007-payment-timeout` |
| `release/` | `develop` | `main`+`develop` | PI release candidate | `release/pi-03` |
| `chore/` | `develop` | `develop` | No story (deps, config) | `chore/update-node-lts` |

Rules: lowercase, hyphens only, artifact ID required (except `chore/`), max 60 chars.

## Commit Message — Always Follow This

```
<type>(<scope>): <subject> [ARTIFACT-NNN]
```

**Types:** `feat` `fix` `bugfix` `docs` `refactor` `test` `ci` `chore` `perf` `revert` `spike` `enabler` `security`

**Scopes:** `portfolio` `large-solution` `program` `team` `devops` `api` `ui` `db` `auth` `infra` `deps`

**Rules:**
- Subject: imperative mood, present tense, max 72 chars, no trailing period
- Artifact ID in brackets at end of subject line: `[STORY-042]`
- Body: explain *why*, not *what*, wrap at 100 chars
- Breaking changes: `BREAKING CHANGE:` in footer

**When Copilot CLI generates a commit, always append:**
```
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
```

## Pull Request — Creation Checklist

Before creating a PR:
1. `git rebase origin/develop` — keep branch up to date (or `origin/main` for hotfix)
2. Run tests locally — all must pass
3. `/diff` in Copilot CLI — review own changes
4. `/review` in Copilot CLI — AI code review
5. For `coverity/` — attach Coverity scan report
6. For `polaris/` — attach Polaris compliance report
7. For `cato/` — notify Cybersecurity Officer

PR title = squash-merge commit message (same format as commit):
```
feat(team): add user login form with email validation [STORY-042]
bugfix(api): fix null dereference in cart service [STORY-099]
security(devops): resolve Polaris findings for PI-03 [PI-03]
```

PR body must include:
- `Closes STORY-NNN` (or `Closes FEAT-NNN` / `Resolves INC-NNN`) — links to backlog item
- Filled description template from `.github/pull_request_template.md`

## Merge Strategy

| Scenario | Strategy | Who |
|---|---|---|
| `story/`, `feature/`, `bugfix/`, `fix/` → `develop` | **Squash and merge** | Dev Team Lead |
| `coverity/`, `polaris/`, `cato/` → `develop` | **Squash and merge** | QA/Security/CyberSec Officer |
| `release/PI-NN` → `main` | **Merge commit** | Release Manager |
| `release/PI-NN` → `develop` | **Merge commit** | Dev Team Lead (after main merge) |
| `hotfix/` → `main` | **Merge commit** | Release Manager |
| `hotfix/` → `develop` | **Merge commit** | Dev Team Lead (immediately after main) |
| Updating a branch with base | **Rebase** (never merge) | Developer |

## Hotfix Fast-Track

For Sev-1/Sev-2 incidents:
1. Branch from `main`: `hotfix/inc-NNN-description`
2. Fix, test, 1 reviewer minimum + Release Manager
3. Merge to `main` AND immediately back-merge to `develop`
4. Create postmortem from `prompts/devops/incident-postmortem.md`

## When to Ask Before Committing

- Changing > 500 lines → split into smaller PRs or ask the RTE (Gandalf)
- Touching auth, payments, or PII → always request Iron Man review
- Adding a new dependency → run `npm audit` / `pip-audit` first
- Breaking API contract → add `BREAKING CHANGE:` footer, notify consumers
- Coverity/Polaris findings → consult QA Engineer or Security Engineer before resolving

## Full Reference

See `git-flow/` for complete documentation:
- `git-flow/README.md` — overall strategy, branch lifecycle, roles
- `git-flow/GitFlow.md` — branch types, creation, merge procedures, role details
- `git-flow/branch-naming.md` — naming rules and examples
- `git-flow/commit-messages.md` — format, types, scopes, examples
- `git-flow/pull-request-rules.md` — PR creation, review, merge rules per branch type

---
applyTo: "**"
---

# Git Flow Instructions

<!-- Loaded automatically by Copilot CLI for all files — git operations -->

## Branch Naming — Always Follow This

```
<type>/<artifact-id>-<short-description>
```

| Type | For | Example |
|---|---|---|
| `story/` | User Story | `story/story-042-add-login-form` |
| `feature/` | Feature (multi-story) | `feature/feat-012-sso-integration` |
| `enabler/` | Technical enabler | `enabler/feat-015-db-migration` |
| `spike/` | Research spike | `spike/story-088-evaluate-graphql` |
| `fix/` | Bug fix | `fix/story-099-null-pointer-checkout` |
| `hotfix/` | Production incident | `hotfix/inc-007-payment-timeout` |
| `release/` | PI release candidate | `release/pi-03` |
| `chore/` | No story (deps, config) | `chore/update-node-lts` |

Rules: lowercase, hyphens only, artifact ID required (except `chore/`), max 60 chars.

## Commit Message — Always Follow This

```
<type>(<scope>): <subject> [ARTIFACT-NNN]
```

**Types:** `feat` `fix` `docs` `refactor` `test` `ci` `chore` `perf` `revert` `spike` `enabler`

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
1. `git rebase origin/main` — keep branch up to date
2. Run tests locally — all must pass
3. `/diff` in Copilot CLI — review own changes
4. `/review` in Copilot CLI — AI code review

PR title = squash-merge commit message (same format as commit):
```
feat(team): add user login form with email validation [STORY-042]
```

PR body must include:
- `Closes STORY-NNN` (or `Closes FEAT-NNN`) — links to backlog item
- Filled description template from `.github/pull_request_template.md`

## Merge Strategy

| Scenario | Strategy |
|---|---|
| `story/`, `feature/`, `fix/` → `main` | **Squash and merge** |
| `hotfix/` → `release/PI-NN` | **Merge commit** |
| Updating a branch with `main` | **Rebase** (never merge) |

## Hotfix Fast-Track

For Sev-1/Sev-2 incidents:
1. Branch from `main`: `hotfix/inc-NNN-description`
2. Fix, test, 1 reviewer minimum
3. Merge to `main` AND cherry-pick to active `release/PI-NN`
4. Create postmortem from `prompts/devops/incident-postmortem.md`

## When to Ask Before Committing

- Changing > 500 lines → split into smaller PRs or ask the RTE (Gandalf)
- Touching auth, payments, or PII → always request Iron Man review
- Adding a new dependency → run `npm audit` / `pip-audit` first
- Breaking API contract → add `BREAKING CHANGE:` footer, notify consumers

## Full Reference

See `git-flow/` for complete documentation:
- `git-flow/README.md` — overall strategy and branch lifecycle
- `git-flow/branch-naming.md` — naming rules and examples
- `git-flow/commit-messages.md` — format, types, scopes, examples
- `git-flow/pull-request-rules.md` — PR creation, review, and merge rules

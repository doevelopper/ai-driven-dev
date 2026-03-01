# Pull Request Rules & Merge Request Guide

A Pull Request (PR) is a **quality gate**, a **knowledge-sharing event**, and a **traceability link** between code and SAFe backlog. These rules ensure every merge into `main` maintains built-in quality.

---

## PR Title Format

```
<type>(<scope>): <subject> [<artifact-id>]
```

The PR title must match the **commit message format** (it becomes the squash-merge commit message):

```
feat(team): add user login form with email validation [STORY-042]
fix(api): resolve null pointer on empty cart [STORY-099]
feat(program): add WSJF calculator to program backlog [FEAT-007]
ci(devops): add SAST scan to GitHub Actions [PI-03]
```

> ✅ PR title is validated by CI (same commitlint rules as commits)

---

## PR Size Rules

| Size | Lines Changed | Policy |
|---|---|---|
| XS | < 50 | Fast-track: 1 reviewer, 4h SLA |
| S | 50–200 | Standard: 2 reviewers, 8h SLA |
| M | 200–500 | Standard: 2 reviewers, 24h SLA |
| L | 500–1000 | Must split if possible; 2 reviewers + architect |
| XL | > 1000 | 🚫 Requires RTE/Tech Lead approval to proceed; split strongly encouraged |

---

## PR Creation Rules

### Before Opening a PR

- [ ] Branch is up to date with `main` (`git rebase origin/main`)
- [ ] All CI checks pass locally (`npm test`, `npm run lint`, etc.)
- [ ] Story/Feature acceptance criteria are all met
- [ ] No `console.log` / debug artifacts left in code
- [ ] Self-review completed (use `/diff` + `/review` in Copilot CLI)

### Opening the PR

1. Use `gh pr create --fill` or the GitHub UI
2. Fill the **PR description template** (`.github/pull_request_template.md`)
3. Assign yourself as author
4. Request reviewers:
   - **Wolverine (Senior Dev)** for all code changes
   - **Iron Man (DevOps)** for CI/CD, infrastructure, security changes
   - **Hermione (PO)** for story acceptance (optional, async)
   - **Legolas / Q** for architectural changes
5. Link the related SAFe artifact:
   - Use `Closes STORY-NNN` or `Closes FEAT-NNN` in the PR body

---

## PR Description Template

> The template is auto-loaded from `.github/pull_request_template.md`

---

## Reviewer Responsibilities

### Code Reviewer (Wolverine / Legolas)

Review for:
- [ ] Logic correctness — does it do what the story requires?
- [ ] Edge cases handled
- [ ] No obvious security issues (injection, auth bypass, data exposure)
- [ ] Tests written and meaningful
- [ ] Code readable and maintainable (no magic numbers, no long methods)
- [ ] No performance regressions introduced
- [ ] Naming follows conventions (`git-flow/branch-naming.md`)

### DevOps Reviewer (Iron Man) — when CI/infra changed

- [ ] Pipeline changes are tested in a branch environment
- [ ] No secrets or credentials in code or env vars
- [ ] Container image scanned (no critical CVEs)
- [ ] Rollback plan documented

### PO Review (Hermione) — optional, async

- [ ] Feature behavior matches acceptance criteria
- [ ] UI/UX matches design (if applicable)
- [ ] Edge cases acceptable to end users

---

## Review Comment Etiquette

Use prefixes to classify comments:

| Prefix | Meaning | Action Required |
|---|---|---|
| `[BLOCK]` | Must fix before merge | Author must address |
| `[SUGGEST]` | Non-blocking improvement | Author may address or explain |
| `[QUESTION]` | Seeking understanding | Author responds; may lead to a fix |
| `[NITPICK]` | Minor style/preference | Author's discretion |
| `[PRAISE]` | Good work highlight | No action needed |

> Never leave a review without at least one `[PRAISE]` — psychological safety matters.

---

## Merge Strategy

| Target | Strategy | Rule |
|---|---|---|
| `main` | **Squash and merge** | One clean commit per story/PR |
| `release/PI-NN` | **Merge commit** | Preserves hotfix history |
| Between branches | **Rebase** | Keep linear history; no merge commits |

### Why Squash?

- `main` history reads like the SAFe backlog: one commit per story
- Bisecting is easier
- Reverts are clean (revert one story at a time)

---

## Merge Requirements (enforced by GitHub)

- ✅ All CI checks green (lint, unit tests, SAST, build)
- ✅ At least **2 approvals** (1 for XS PRs)
- ✅ No unresolved review conversations
- ✅ Branch up to date with `main`
- ✅ PR title passes commitlint
- ✅ PR linked to a SAFe artifact (`Closes STORY-NNN` present)

---

## Post-Merge Checklist

- [ ] Branch auto-deleted (GitHub setting)
- [ ] Story moved to "Done" in issue tracker / board
- [ ] CI deploy to `dev` / `test` triggered and green
- [ ] If Feature is complete: System Demo updated in `program/system-demo/README.md`

---

## Hotfix Fast-Track

For Sev-1 / Sev-2 incidents, a **hotfix fast-track** applies:

1. Branch: `hotfix/inc-NNN-short-description` from `main`
2. 1 reviewer minimum (Iron Man or Wolverine on-call)
3. CI must still pass
4. Merged to `main` AND cherry-picked to active `release/PI-NN`
5. Incident postmortem created within 24h (use `prompts/devops/incident-postmortem.md`)

---

## Copilot CLI Integration

```bash
# Before opening a PR — review your own changes
/diff
/review

# Generate a PR description based on changes
# "Summarize my changes for STORY-042 as a PR description"

# After CI fails — debug
# "Why is the SAST scan failing in the CI pipeline?"
```

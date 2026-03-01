# Pull Request Rules & Merge Request Guide

A Pull Request (PR) is a **quality gate**, a **knowledge-sharing event**, and a **traceability link** between code and SAFe backlog. These rules ensure every merge maintains built-in quality.

---

## PR Title Format

```
<type>(<scope>): <subject> [<artifact-id>]
```

The PR title must match the **commit message format** (it becomes the squash-merge commit message):

```
feat(team): add user login form with email validation [STORY-042]
fix(api): resolve null pointer on empty cart [STORY-099]
bugfix(api): fix null dereference in cart service [STORY-099]
feat(program): add WSJF calculator to program backlog [FEAT-007]
ci(devops): add SAST scan to GitHub Actions [PI-03]
security(devops): resolve Polaris findings for PI-03 [PI-03]
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

## Merge Target Rules

| Source Branch | Target Branch | Strategy | Who Approves | Prerequisites |
|---|---|---|---|---|
| `feature/` | `develop` | **Squash and merge** | Dev Team Lead + 1 reviewer | Tests pass, AC met, code reviewed |
| `story/` | `develop` | **Squash and merge** | Dev Team Lead or Senior Dev | Tests pass, AC met |
| `bugfix/` | `develop` | **Squash and merge** | Dev Team Lead or Senior Dev | Bug reproduced, fixed, tested |
| `enabler/` | `develop` | **Squash and merge** | Architect + Dev Team Lead | Arch review, tests pass |
| `spike/` | `develop` | **Squash and merge** | Architect | Findings documented |
| `fix/` | `develop` | **Squash and merge** | 1 reviewer | Tests pass |
| `coverity/` | `develop` | **Squash and merge** | QA Engineer | All Coverity defects resolved, report attached |
| `polaris/` | `develop` | **Squash and merge** | Security Engineer | All Polaris findings resolved or accepted |
| `cato/` | `develop` | **Squash and merge** | Cybersecurity Officer | All cyber risks mitigated, ATO documented |
| `chore/` | `develop` | **Squash and merge** | 1 reviewer | CI passes |
| `release/PI-NN` | `main` | **Merge commit** | Release Manager + 2 reviewers | All tests pass, system demo done, BO sign-off |
| `release/PI-NN` | `develop` | **Merge commit** | Dev Team Lead | After merging to `main` |
| `hotfix/` | `main` | **Merge commit** | Release Manager + 1 on-call | CI passes, incident linked |
| `hotfix/` | `develop` | **Merge commit** | Dev Team Lead | After merging to `main` |

### Why Squash into `develop`?

- `develop` history reads like the SAFe backlog: one commit per story/bugfix
- Bisecting is easier
- Reverts are clean (revert one story at a time)

### Why Merge Commit into `main`?

- Preserves the full release/hotfix history
- Enables precise rollback of an entire release
- `main` commit graph clearly shows release boundaries

---

## PR Creation Rules

### Before Opening a PR

- [ ] Branch is up to date with its base (`git rebase origin/develop` or `origin/main` for hotfix)
- [ ] All CI checks pass locally (`npm test`, `npm run lint`, etc.)
- [ ] Story/Feature acceptance criteria are all met
- [ ] No `console.log` / debug artifacts left in code
- [ ] Self-review completed (use `/diff` + `/review` in Copilot CLI)
- [ ] For `coverity/`: Coverity scan report attached or linked
- [ ] For `polaris/`: Polaris compliance report attached or linked
- [ ] For `cato/`: Cybersecurity risk register updated and Officer notified

### Opening the PR

1. Use `gh pr create --base develop --fill --assignee @me` (or `--base main` for hotfix/release)
2. Fill the **PR description template** (`.github/pull_request_template.md`)
3. Assign yourself as author
4. Request reviewers per type:

| PR Type | Required Reviewers |
|---|---|
| `feature/`, `story/`, `fix/` | Wolverine (Senior Dev) + Dev Team Lead |
| `bugfix/` | Wolverine (Senior Dev) |
| `enabler/` | Legolas / Q (Architect) + Dev Team Lead |
| `coverity/` | QA Engineer (mandatory) + Dev Team Lead |
| `polaris/` | Iron Man (Security) + Dev Team Lead |
| `cato/` | Cybersecurity Officer (mandatory) + Release Manager |
| `release/PI-NN → main` | Release Manager + RTE (Gandalf) + Business Owner |
| `hotfix/` | Iron Man or Wolverine (on-call) + Release Manager |

5. Link the related SAFe artifact:
   - Use `Closes STORY-NNN`, `Closes FEAT-NNN`, or `Resolves INC-NNN` in the PR body

---

## PR Description Template

> The template is auto-loaded from `.github/pull_request_template.md`

---

## Reviewer Responsibilities

### Code Reviewer (Wolverine / Legolas)

- [ ] Logic correctness — does it do what the story requires?
- [ ] Edge cases handled
- [ ] No obvious security issues (injection, auth bypass, data exposure)
- [ ] Tests written and meaningful
- [ ] Code readable and maintainable (no magic numbers, no long methods)
- [ ] No performance regressions introduced
- [ ] Naming follows conventions (`git-flow/branch-naming.md`)

### DevOps / Security Reviewer (Iron Man) — for CI/infra/security changes

- [ ] Pipeline changes are tested in a branch environment
- [ ] No secrets or credentials in code or env vars
- [ ] Container image scanned (no critical CVEs)
- [ ] Rollback plan documented

### QA Engineer — for `coverity/` branches

- [ ] All Coverity defects (Critical, High) are resolved
- [ ] Coverity scan report attached to PR
- [ ] No new defects introduced vs. previous scan baseline
- [ ] False positives documented with justification

### Security Engineer — for `polaris/` branches

- [ ] All Polaris security findings resolved or risk-accepted
- [ ] Polaris compliance report attached to PR
- [ ] No new vulnerabilities introduced
- [ ] Accepted risks documented with justification and approver

### Cybersecurity Officer — for `cato/` branches

- [ ] Full cybersecurity risk assessment completed
- [ ] All identified risks are mitigated or formally accepted
- [ ] ATO (Authorization To Operate) document updated
- [ ] Sign-off recorded in PR

### Release Manager — for `release/PI-NN → main`

- [ ] All system demo objectives met
- [ ] Release notes prepared
- [ ] Rollback plan documented
- [ ] Business Owner sign-off obtained
- [ ] Tag created (`vN.N.N`)
- [ ] Back-merge to `develop` planned

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

## Merge Requirements (enforced by GitHub)

### `develop` (all feature/story/bugfix/quality branches)
- ✅ All CI checks green (lint, unit tests, SAST, build)
- ✅ At least **1 approval** (Dev Team Lead or Senior Dev)
- ✅ No unresolved review conversations
- ✅ Branch up to date with `develop`
- ✅ PR title passes commitlint
- ✅ PR linked to a SAFe artifact

### `main` (release and hotfix only)
- ✅ All CI checks green
- ✅ At least **2 approvals** (including Release Manager)
- ✅ No unresolved review conversations
- ✅ Branch up to date with `main`
- ✅ PR title passes commitlint
- ✅ Release Manager sign-off documented

---

## Post-Merge Checklist

- [ ] Branch auto-deleted (GitHub setting)
- [ ] Story/artifact moved to "Done" in issue tracker / board
- [ ] CI deploy triggered and green
- [ ] For `release/PI-NN → main`: back-merge release branch into `develop`
- [ ] For `hotfix/`: back-merge into `develop` immediately after `main` merge
- [ ] If Feature complete: System Demo updated in `program/system-demo/README.md`

---

## Hotfix Fast-Track

For Sev-1 / Sev-2 incidents, a **hotfix fast-track** applies:

1. Branch: `hotfix/inc-NNN-short-description` from **`main`**
2. 1 reviewer minimum (Iron Man or Wolverine on-call) + Release Manager
3. CI must still pass
4. Merged to `main` AND **immediately back-merged to `develop`**
5. Tag applied if patch version bump needed (`vN.N.N+1`)
6. Incident postmortem created within 24h (use `prompts/devops/incident-postmortem.md`)

---

## Copilot CLI Integration

```bash
# Before opening a PR — review your own changes
/diff
/review

# Generate a PR description based on changes
# "Summarize my changes for STORY-042 as a PR description targeting develop"

# After CI fails — debug
# "Why is the SAST scan failing in the CI pipeline?"

# For Coverity/Polaris PRs
# "Summarize the Coverity defects I resolved in this branch"
# "List the Polaris findings addressed in this PR"
```

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

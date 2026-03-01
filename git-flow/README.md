# Git Flow — AI-Driven SAFe 6.0

This document defines the Git workflow, branching strategy, and collaboration model for this repository. It aligns **GitFlow** with **SAFe 6.0 cadences** and supports **AI-driven development** via GitHub Copilot CLI.

---

## Strategy: GitFlow with SAFe PI Release Cadence

We use **GitFlow** as the primary model: `main` holds production-ready code, `develop` is the active integration branch, and short-lived branches handle features, fixes, and quality-gate checks.

```
  main  ──────────────────────────────────────────────────────────────►  production
    │  ▲                                                          ▲
    │  │ merge (Release Manager)                  hotfix merged   │
    │  │                                          to main+develop │
    ▼  │                                                          │
  develop ────────────────────────────────────────────────────────►  integration
    │  ▲    ▲       ▲         ▲          ▲        ▲
    │  │    │       │         │          │        │
    │  │  feature/ bugfix/ coverity/ polaris/  cato/
    │  │  (Feature (Bugs)  (SAST)   (SecComp) (CyberAuth)
    │  │   Dev)
    │  │
    └──────► release/PI-NN  (cut from develop at IP Iteration)
             │  └─► hardening, final tests, demo prep
             └──►  tag vN.N.N → merge to main → deploy to production
```

### Branch Lifecycle Rules

| Branch | Base | Merge Target | Lifetime | Who | Auto-deleted? |
|---|---|---|---|---|---|
| `main` | — | — | Permanent | Release Manager | ❌ |
| `develop` | `main` | — | Permanent | Dev Team Lead | ❌ |
| `feature/` | `develop` | `develop` | ≤ 3 days | Feature Developer | ✅ after merge |
| `story/` | `develop` | `develop` | ≤ 2 days | Feature Developer | ✅ after merge |
| `bugfix/` | `develop` | `develop` | ≤ 1 day | Bugfix Developer | ✅ after merge |
| `enabler/` | `develop` | `develop` | ≤ 3 days | Architect | ✅ after merge |
| `spike/` | `develop` | `develop` | ≤ 5 days | Architect | ✅ after merge |
| `fix/` | `develop` | `develop` | ≤ 1 day | Developer | ✅ after merge |
| `coverity/` | `develop` | `develop` | ≤ 2 days | QA Engineer | ✅ after merge |
| `polaris/` | `develop` | `develop` | ≤ 2 days | Security Engineer | ✅ after merge |
| `cato/` | `develop` | `develop` | ≤ 5 days | Cybersecurity Officer | ✅ after merge |
| `release/PI-NN` | `develop` | `main` + `develop` | PI duration | Release Manager | ❌ kept for history |
| `hotfix/` | `main` | `main` + `develop` | Hours | On-call Dev / DevOps | ✅ after merge |
| `chore/` | `develop` | `develop` | ≤ 1 day | DevOps | ✅ after merge |

### Why a `develop` Branch?

`develop` acts as the **continuous integration hub** for all work-in-progress:
- Features, bugfixes, and quality-gate branches integrate here before reaching production
- `main` always reflects what is **in production** — never a work-in-progress state
- Enables parallel quality checks (Coverity, Polaris, CATO) without polluting the production line
- Aligns with SAFe's **built-in quality** principle: code must pass all gates before release

---

## Branch Purpose Details

| Branch | Purpose | Prerequisites to Merge |
|---|---|---|
| **main** | Production-ready code. Always deployable. | Merge from `release/PI-NN` only. All tests pass. Code reviewed. Release Manager sign-off. |
| **develop** | Active integration. All features land here first. | All tests pass. No critical issues. Code reviewed. Dev Team Lead approval. |
| **feature/** | New feature development. | Feature fully developed, tested, reviewed. All tests pass. |
| **bugfix/** | Fix development defects found in `develop`. | Bug resolved, tested, reviewed. All tests pass. |
| **story/** | Single user story implementation. | Story AC met, code reviewed, tests passing. |
| **enabler/** | Technical enabler (infra, refactor, architecture). | Tests pass, architect sign-off. |
| **spike/** | Time-boxed research. Output: findings doc, no prod code. | Findings documented, time-box respected. |
| **fix/** | Bug fix tracked as a story. | Bug resolved and tested. |
| **coverity/** | Static code analysis (Coverity SAST). | All identified defects addressed. Analysis report attached to PR. |
| **polaris/** | Security & compliance checks (Polaris). | All security/compliance issues resolved. Polaris report clean or accepted. |
| **cato/** | Cybersecurity Authorization To Operate process. | All cyber risks mitigated. Cybersecurity Officer sign-off. |
| **release/PI-NN** | PI release candidate. Hardening and final validation. | All tests pass, system demo completed, Business Owner sign-off. |
| **hotfix/** | Urgent production fix (Sev-1/Sev-2). | CI passes, 1 reviewer minimum, incident linked. |

---

## Roles & Responsibilities

| Role | SAFe Persona | Branch Ownership |
|---|---|---|
| Release Manager | Apollo (Portfolio) | Merges `release/PI-NN` → `main`. Signs off production deployments. |
| Dev Team Lead | Gandalf (RTE) / Wolverine (Senior Dev) | Manages `develop` integration. Approves feature merges. |
| Feature Developer | Wolverine / Team Members | Creates and merges `feature/`, `story/`, `fix/` branches. |
| Bugfix Developer | Wolverine / Team Members | Creates and merges `bugfix/` branches. |
| QA Engineer | Team Member (QA role) | Creates and merges `coverity/` branches. Validates static analysis. |
| Security Engineer | Iron Man (DevOps) | Creates and merges `polaris/` branches. Validates security compliance. |
| Cybersecurity Officer | Iron Man / External | Creates and merges `cato/` branches. Issues ATO sign-off. |

---

## Environment ↔ Branch Mapping

| Environment | Branch / Tag | Deploy Trigger |
|---|---|---|
| `dev` | `develop` | Every merge to `develop` (automatic) |
| `test` | `develop` | After integration tests pass on `develop` |
| `staging` | `release/PI-NN` | Manual — Release Manager approval |
| `production` | `main` + tag `vN.N.N` | Manual — Business Owner sign-off |

---

## PI Release Flow

```
PI Planning
    │
    ├─ Iterations 1–4: features/stories merge into develop continuously
    │   ├── Coverity scans run per iteration (coverity/ branches)
    │   ├── Polaris checks run per PI (polaris/ branches)
    │   └── CATO assessment runs as needed (cato/ branches)
    │
    ├─ IP Iteration: cut release/PI-NN from develop
    │   ├── Hardening, final tests, system demo prep
    │   └── Hotfixes go to main AND back-merged to develop
    │
    └─ PI End: Release Manager merges release/PI-NN → main
               tag vN.N.N → deploy to production
               back-merge release/PI-NN → develop
```

---

## Protection Rules (GitHub Branch Protection)

### `main`
- ✅ Require pull request (no direct push — ever)
- ✅ Require at least **2 approvals** (including Release Manager)
- ✅ Require all status checks to pass (CI pipeline)
- ✅ Require branches to be up to date before merging
- ✅ Dismiss stale PR approvals on new commits
- ✅ Require signed commits
- ✅ Include administrators

### `develop`
- ✅ Require pull request
- ✅ Require at least **1 approval** (Dev Team Lead or Senior Dev)
- ✅ Require CI checks to pass
- ✅ Dismiss stale approvals on new commits

### `release/PI-*`
- ✅ Require pull request
- ✅ Require at least **2 approvals** (including RTE or Release Manager)
- ✅ No force-push
- ✅ Lock branch after tagging and merging to `main`

---

## Gitflow Cheatsheet

```bash
# ── Feature / Story work ──────────────────────────────────────────
git checkout develop && git pull
git checkout -b feature/feat-012-sso-integration
# ... develop ...
git push origin feature/feat-012-sso-integration
gh pr create --base develop --fill --assignee @me

# ── Bugfix ────────────────────────────────────────────────────────
git checkout develop && git pull
git checkout -b bugfix/story-099-null-pointer-checkout
# ... fix ...
gh pr create --base develop --fill --assignee @me

# ── Static Analysis (Coverity) ────────────────────────────────────
git checkout develop && git pull
git checkout -b coverity/pi-03-iter-02-scan
# ... resolve Coverity defects ...
gh pr create --base develop --fill --assignee @me

# ── Security Check (Polaris) ──────────────────────────────────────
git checkout develop && git pull
git checkout -b polaris/pi-03-security-scan
# ... resolve Polaris findings ...
gh pr create --base develop --fill --assignee @me

# ── CATO ──────────────────────────────────────────────────────────
git checkout develop && git pull
git checkout -b cato/pi-03-ato-assessment
# ... cyber risk mitigation ...
gh pr create --base develop --fill --assignee @me

# ── Keep branch up to date ────────────────────────────────────────
git fetch origin && git rebase origin/develop

# ── Cut a release branch (IP Iteration) ──────────────────────────
git checkout develop && git pull
git checkout -b release/pi-03
git push origin release/pi-03
# ... hardening ...
gh pr create --base main --title "release(program): PI-03 release [PI-03]" --assignee @me

# ── Tag and finish release ────────────────────────────────────────
git checkout main && git pull
git tag -a v3.0.0 -m "PI-03 release"
git push origin main --tags
# Back-merge release into develop
git checkout develop && git merge --no-ff release/pi-03
git push origin develop

# ── Hotfix (production incident) ──────────────────────────────────
git checkout main && git pull
git checkout -b hotfix/inc-007-payment-api-timeout
# ... fix ...
gh pr create --base main --fill --assignee @me
# After merge to main → back-merge to develop
git checkout develop && git merge --no-ff hotfix/inc-007-payment-api-timeout
```

---

## Related Files

| File | Purpose |
|---|---|
| `git-flow/branch-naming.md` | Detailed naming rules and examples |
| `git-flow/commit-messages.md` | Commit message format and examples |
| `git-flow/pull-request-rules.md` | PR creation, review, and merge rules |
| `.github/pull_request_template.md` | Auto-loaded PR description template |
| `.github/instructions/git-flow.instructions.md` | Copilot CLI git instructions |

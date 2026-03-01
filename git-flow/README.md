# Git Flow — AI-Driven SAFe 6.0

This document defines the Git workflow, branching strategy, and collaboration model for this repository. It is designed to align **Git flow** with **SAFe 6.0 cadences** and support **AI-driven development** via GitHub Copilot CLI.

---

## Strategy: Trunk-Based Development with PI Release Branches

We use **trunk-based development** as the primary model, extended with PI-aligned release branches and a short-lived feature branch per SAFe work item.

```
                        ┌─────────────────────────────────────────────┐
                        │                    main (trunk)              │
                        │  always deployable — protected, auto-builds  │
                        └───────┬─────────────────────────────────────┘
                                │
           ┌────────────────────┼────────────────────┐
           │                    │                    │
    feature/FEAT-NNN      story/STORY-NNN      hotfix/INC-NNN
    (from main, ≤ 3 days)  (from main, ≤ 2 days)  (from main, hours)
           │                    │                    │
           └──── PR → main ─────┘                    └─── PR → main
                                │
                         release/PI-NN              (tagged at PI end)
                         (cut from main, hardened)
```

### Branch Lifecycle Rules

| Branch Type | Base | Lifetime | Merge Target | Auto-deleted? |
|---|---|---|---|---|
| `feature/` | `main` | ≤ 3 days | `main` | ✅ after merge |
| `story/` | `main` | ≤ 2 days | `main` | ✅ after merge |
| `enabler/` | `main` | ≤ 3 days | `main` | ✅ after merge |
| `spike/` | `main` | ≤ 5 days | `main` | ✅ after merge |
| `fix/` | `main` | ≤ 1 day | `main` | ✅ after merge |
| `hotfix/` | `main` | Hours | `main` + `release/` | ✅ after merge |
| `release/PI-NN` | `main` | PI duration | — (tag only) | ❌ kept for history |
| `chore/` | `main` | ≤ 1 day | `main` | ✅ after merge |

### Why Not Long-Lived Feature Branches?

Long-lived branches cause **merge hell** and contradict SAFe's built-in quality principle:
- Stories must be done (tested, integrated) every iteration
- CI must run on every commit
- The system must be demo-ready at any time

---

## Environment ↔ Branch Mapping

| Environment | Branch / Tag | Deploy Trigger |
|---|---|---|
| `dev` | `main` | Every merge to `main` (automatic) |
| `test` | `main` | Every merge to `main` (after integration tests) |
| `staging` | `release/PI-NN` | Manual — release manager approval |
| `production` | `release/PI-NN` + tag `vN.N.N` | Manual — Business Owner sign-off |

---

## PI Release Flow

```
PI Planning
    │
    ├─ Iterations 1–5: stories merge into main continuously
    │
    ├─ IP Iteration: cut release/PI-NN from main
    │   ├── Hardening, final tests, demo prep
    │   └── Hotfixes go to both main and release/PI-NN
    │
    └─ PI End: tag release/PI-NN as vN.N.N → deploy to production
```

---

## Protection Rules (GitHub Branch Protection)

### `main`
- ✅ Require pull request (no direct push)
- ✅ Require at least **2 approvals**
- ✅ Require all status checks to pass (CI pipeline)
- ✅ Require branches to be up to date before merging
- ✅ Dismiss stale pull request approvals on new commits
- ✅ Require signed commits
- ✅ Include administrators

### `release/PI-*`
- ✅ Require pull request
- ✅ Require at least **2 approvals** (including RTE or Release Manager)
- ✅ No force-push
- ✅ Lock branch after tagging

---

## Gitflow Cheatsheet

```bash
# Start a story branch
git checkout main && git pull
git checkout -b story/STORY-042-user-login-form

# Start a feature branch (spans multiple stories)
git checkout -b feature/FEAT-012-sso-integration

# Start a hotfix
git checkout main && git pull
git checkout -b hotfix/INC-007-payment-timeout

# Keep branch up to date (prefer rebase over merge)
git fetch origin
git rebase origin/main

# Open a PR (GitHub CLI)
gh pr create --fill --assignee @me

# After merge: clean up
git checkout main && git pull
git branch -d story/STORY-042-user-login-form

# Cut a release branch at end of PI
git checkout main && git pull
git checkout -b release/PI-03
git tag -a v3.0.0 -m "PI-03 release"
git push origin release/PI-03 --tags
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

# Commit Message Convention

We follow **Conventional Commits 1.0** extended with **SAFe artifact references** to enable automated changelog generation, release notes, and full traceability from code to backlog.

---

## Format

```
<type>(<scope>): <subject> [<artifact-id>]

[optional body]

[optional footer(s)]
```

### Components

| Part | Required | Rules |
|---|---|---|
| `<type>` | ✅ | Lowercase, from the allowed list below |
| `(<scope>)` | ✅ | SAFe level or component name |
| `<subject>` | ✅ | Imperative, present tense, max 72 chars, no period |
| `[<artifact-id>]` | ✅ | SAFe ID in brackets at end of subject line |
| `body` | When needed | Explains *why*, not *what*; wrap at 100 chars |
| `footer` | When needed | `BREAKING CHANGE:`, `Closes`, `Co-authored-by:` |

---

## Allowed Types

| Type | When to Use | Triggers |
|---|---|---|
| `feat` | New feature or story implementation | Minor version bump |
| `fix` | Bug fix | Patch version bump |
| `docs` | Documentation only | — |
| `refactor` | Code restructuring — no behavior change | — |
| `test` | Adding or updating tests | — |
| `ci` | CI/CD pipeline or DevOps changes | — |
| `chore` | Build system, dependencies, config | — |
| `perf` | Performance improvement | Patch version bump |
| `revert` | Reverting a previous commit | — |
| `spike` | Spike / research output (findings only) | — |
| `enabler` | Technical enabler work (infra, architecture) | — |

---

## Allowed Scopes

Scopes map to **SAFe levels and technical components**:

| Scope | When to Use |
|---|---|
| `portfolio` | Changes to portfolio artifacts or processes |
| `large-solution` | Solution train artifacts, capabilities |
| `program` | ART-level features, PI planning, program backlog |
| `team` | Team-level stories, iterations, ceremonies |
| `devops` | CI/CD, infrastructure, deployment |
| `metrics` | OKRs, dashboards, flow metrics |
| `api` | API layer changes |
| `ui` | Frontend / UI changes |
| `db` | Database schema or migration |
| `auth` | Authentication or authorization |
| `infra` | Infrastructure as code |
| `deps` | Dependency updates |

> Use the most specific scope. Combine if needed: `api/auth`

---

## Examples

### Story implementation
```
feat(team): add user login form with email validation [STORY-042]

Implements the login UI using React Hook Form with Zod validation schema.
Error messages follow the design system token conventions.

Closes STORY-042
```

### Bug fix
```
fix(api): resolve null pointer on empty cart checkout [STORY-099]

The cart summary endpoint crashed when the cart had 0 items.
Added a guard clause before accessing cart.items[0].

Closes STORY-099
```

### Enabler / refactoring
```
enabler(infra): migrate database connection pool to PgBouncer [FEAT-015]

PgBouncer reduces connection overhead under high load.
See ADR-004 for decision rationale.
```

### CI/CD change (Iron Man)
```
ci(devops): add Trivy container scan to GitHub Actions pipeline

Scans the Docker image after build, fails on CRITICAL severity.
Part of DevSecOps hardening for PI-03.
```

### Breaking change
```
feat(api): replace v1 auth tokens with short-lived JWTs [FEAT-021]

BREAKING CHANGE: /auth/token endpoint response schema changed.
Old `token` field replaced by `access_token` + `refresh_token`.
Consumers must update before PI-03 release.

Migration guide: docs/migration-v2-auth.md
```

### Hotfix (Iron Man — urgent)
```
fix(api): increase payment gateway timeout from 5s to 30s [INC-007]

Payment API occasionally times out under load.
Temporary fix pending architectural improvement (FEAT-031).
```

### Documentation
```
docs(program): update PI-03 objectives for Team Alpha [PI-03]
```

### Revert
```
revert: feat(ui): new dashboard layout [STORY-077]

Reverts commit abc1234.
Dashboard caused performance regression detected in staging.
Tracked in STORY-081.
```

---

## Multi-Author (Pair / Mob Programming)

When two or more people author a commit, add `Co-authored-by:` trailers:

```
feat(team): implement CSV export for backlog [STORY-055]

Co-authored-by: Wolverine <wolverine@example.com>
Co-authored-by: Hermione <hermione@example.com>
```

---

## Copilot CLI Auto-Commit

When GitHub Copilot CLI generates a commit, it appends:

```
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
```

---

## Rules Enforced by CI (commitlint)

```js
// commitlint.config.js (to be added)
module.exports = {
  extends: ['@commitlint/config-conventional'],
  rules: {
    'type-enum': [2, 'always', [
      'feat','fix','docs','refactor','test','ci',
      'chore','perf','revert','spike','enabler'
    ]],
    'scope-empty': [2, 'never'],       // scope is required
    'subject-max-length': [2, 'always', 100],
    'body-max-line-length': [2, 'always', 100],
  }
};
```

---

## Changelog Generation

Release notes are auto-generated from commit types:

| Section in Changelog | Commit Types |
|---|---|
| 🚀 Features | `feat`, `enabler` |
| 🐛 Bug Fixes | `fix` |
| ⚡ Performance | `perf` |
| 💥 Breaking Changes | any with `BREAKING CHANGE:` footer |
| 🔧 Maintenance | `chore`, `deps`, `ci` |
| 📝 Documentation | `docs` |
| 🧪 Tests | `test` |

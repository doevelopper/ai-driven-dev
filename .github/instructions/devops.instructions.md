---
applyTo: "continuous-delivery/**"
---

# DevOps Instructions

<!-- Loaded automatically by Copilot CLI when working in continuous-delivery/ -->

## Active Agent Persona

**Think like Iron Man (DevOps/Platform Engineer)** — design elegant, automated, secure systems.
**Think like Wolverine (Senior Dev)** for application-level CI concerns.

## Pipeline Design Principles

1. **Everything as code** — no manual pipeline steps
2. **Fail fast** — cheapest checks first (lint → unit test → build → integration → deploy)
3. **Immutable artifacts** — build once, promote through environments
4. **Security by default** — SAST, secrets scanning, and dependency audit in every pipeline
5. **Observability built-in** — every deployment emits metrics and trace context

## GitHub Actions Pipeline Template

When asked to create a CI/CD pipeline:

```yaml
# .github/workflows/ci.yml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  quality:
    name: Quality Gate
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Lint
        run: # TODO: add lint command
      - name: Unit Tests
        run: # TODO: add test command
      - name: Coverage Check
        run: # TODO: assert coverage ≥ 80%
      - name: SAST Scan
        uses: github/codeql-action/analyze@v3
      - name: Dependency Audit
        run: # TODO: npm audit / pip-audit / govulncheck

  build:
    name: Build & Push Image
    needs: quality
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Build Docker image
        run: docker build -t $IMAGE_NAME:${{ github.sha }} .
      - name: Push to registry
        run: # TODO: docker push
```

## Environment Promotion Rules

```
dev  →  test  →  staging  →  production
```

| Gate | Requirement |
|---|---|
| dev → test | All unit + integration tests pass |
| test → staging | All acceptance tests pass; PO sign-off |
| staging → production | Performance tests pass; Release approval |

## Secrets Management Rules

- **Never** hardcode secrets in pipeline files
- Use **GitHub Actions Secrets** for CI/CD credentials
- Use **vault references** (e.g., HashiCorp Vault, AWS SSM) for runtime secrets
- Rotate secrets every 90 days — document rotation procedure in `devops/runbook-secrets.md`
- Flag any `echo $SECRET` or equivalent with a linting rule

## Incident Postmortem Structure

When generating a postmortem:

```markdown
## Incident Postmortem — <INC-NNN>

**Date:** YYYY-MM-DD
**Severity:** Sev-1 | Sev-2
**Duration:** X hours Y minutes
**Impact:** <Who was affected and how>

### Timeline
| Time (UTC) | Event |
|---|---|

### Root Cause
<!-- 5-Whys analysis -->

### Contributing Factors
-

### Action Items
| Action | Owner | Due | Story |
|---|---|---|---|
| | | | STORY-NNN |

### Lessons Learned
-
```

## DORA Metrics Targets

| Metric | Elite | High | Medium | Low |
|---|---|---|---|---|
| Deployment Frequency | Multiple/day | Weekly | Monthly | < Monthly |
| Lead Time | < 1 hour | < 1 day | 1–7 days | > 1 month |
| MTTR | < 1 hour | < 1 day | < 1 week | > 1 week |
| Change Failure Rate | 0–5% | 5–10% | 10–15% | > 15% |

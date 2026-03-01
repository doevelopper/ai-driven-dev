# CI/CD Pipeline

This folder contains pipeline-as-code definitions, branch strategies, and build configurations for the ART.

## Branch Strategy

We follow **trunk-based development** with short-lived feature branches:

```
main (trunk)
 ├── feature/<ticket-id>-<short-description>   # max 1–2 days lifetime
 ├── fix/<ticket-id>-<short-description>
 └── release/<version>                          # optional, for coordinated releases
```

## Pipeline Stages

```
Commit → Build → Unit Test → Static Analysis → Integration Test → Deploy to Dev → Acceptance Test → Deploy to Staging → Performance Test → Deploy to Production (Release on Demand)
```

## Quality Gates per Stage

| Stage | Gate | Failure Action |
|---|---|---|
| Build | Compiles without errors | Block merge |
| Unit Test | All tests pass, ≥80% coverage | Block merge |
| Static Analysis | No new critical issues (SAST/DAST) | Block merge |
| Integration Test | All integration tests pass | Block merge |
| Performance Test | p99 latency < threshold | Alert, review |
| Acceptance Test | All BDD scenarios pass | Block deploy |

## Pipeline Templates

<!-- TODO: Add pipeline template files -->

| Platform | File | Status |
|---|---|---|
| GitHub Actions | `.github/workflows/ci.yml` | TODO |
| GitHub Actions | `.github/workflows/cd.yml` | TODO |

## Feature Flag Strategy

<!-- TODO: Define feature flag tooling and conventions -->

- All new features wrapped in a feature flag
- Flag naming: `<team>.<feature-slug>` (e.g., `team-alpha.new-checkout-flow`)
- Flags reviewed and cleaned up within 2 PIs of release


# Continuous Delivery Pipeline

The Continuous Delivery Pipeline (CDP) enables a fast, reliable flow from code commit to production. It is a core SAFe competency under **Team and Technical Agility** and **Product Development Flow**.

## Four Aspects

| Aspect | Purpose |
|---|---|
| **Continuous Exploration (CE)** | Discover and validate what to build |
| **Continuous Integration (CI)** | Integrate and test code continuously |
| **Continuous Deployment (CD)** | Deploy to staging/production automatically |
| **Release on Demand** | Decouple deployment from business release |

## Sub-folders

| Folder | Content |
|---|---|
| `ci-cd/` | Pipeline definitions, branch strategies, build configs |
| `devops/` | DevSecOps practices, environment configs, runbooks |

## Built-in Quality Gates

1. **Unit tests** — run on every commit
2. **Static analysis / SAST** — automated security scanning
3. **Integration tests** — run on every merge to main
4. **Performance tests** — run at end of iteration
5. **Acceptance tests (BDD)** — validate feature behavior

## Release Strategy

- **Feature flags** decouple deployment from release
- **Canary / Blue-Green deployments** minimize release risk
- **Release on Demand** — business decides when to activate features

## DORA Metrics

| Metric | Target | Current |
|---|---|---|
| Deployment Frequency | Daily or more | TBD |
| Lead Time for Changes | < 1 day | TBD |
| Mean Time to Restore (MTTR) | < 1 hour | TBD |
| Change Failure Rate | < 5% | TBD |

<!-- TODO: Add pipeline-as-code templates (GitHub Actions / Jenkins / GitLab CI) -->

# Prompt: Generate a CI/CD Pipeline

**Persona:** Iron Man (DevOps / Platform Engineer)
**Level:** Team / ART
**Output:** `.github/workflows/ci.yml`, `.github/workflows/cd.yml`

---

## Instructions

<!-- AI: You are Iron Man, DevOps/Platform Engineer. Generate a production-grade CI/CD pipeline following the conventions in .github/instructions/devops.instructions.md. Prioritize security, speed, and immutable artifact promotion. -->

Act as **Iron Man (DevOps)**. Generate a CI/CD pipeline for:

**Service / Application name:** `[SERVICE NAME]`

**Language / Runtime:** `[e.g., TypeScript/Node.js, Python, Go, Java]`

**Package manager:** `[e.g., npm, pip, go modules, Maven]`

**Container registry:** `[e.g., ghcr.io, ECR, GCR]`

**Deployment target:** `[e.g., Kubernetes, AWS ECS, Azure App Service, Lambda]`

**Environments:** `[dev / test / staging / production]`

(optional: Test command: [e.g., npm test])
(optional: Lint command: [e.g., npm run lint])
(optional: Build command: [e.g., npm run build])
(optional: Special security requirements: [DESCRIBE])

---

## Expected Output

### File 1: `.github/workflows/ci.yml`

Quality gate pipeline triggered on every push and PR.

Stages (in order):
1. Lint & static analysis
2. Unit tests + coverage check (≥ 80%)
3. SAST scan (CodeQL)
4. Dependency vulnerability audit
5. Container image build
6. Container image scan (Trivy or similar)

### File 2: `.github/workflows/cd.yml`

Deployment pipeline triggered after CI passes on `main`.

Stages:
1. Deploy to `dev` (automatic)
2. Run integration tests
3. Deploy to `test` (automatic if integration tests pass)
4. Run acceptance tests
5. Deploy to `staging` (manual approval gate)
6. Smoke test staging
7. Deploy to `production` (manual approval gate + release manager sign-off)

### File 3: `continuous-delivery/ci-cd/README.md` update

Add a section documenting:
- Service name and pipeline entry points
- Feature flag strategy for this service
- Rollback procedure

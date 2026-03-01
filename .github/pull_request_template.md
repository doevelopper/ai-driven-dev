## Summary

<!-- Required: 1-3 sentences explaining WHAT this PR does and WHY -->



---

## SAFe Artifact

| Field | Value |
|---|---|
| **Type** | Story / Feature / Enabler / Spike / Fix / Hotfix / Chore |
| **Artifact ID** | `STORY-NNN` / `FEAT-NNN` / `INC-NNN` |
| **PI / Iteration** | `PI-NN / Iter-NN` |
| **Team** | <!-- Your team name --> |

**Closes:** <!-- STORY-NNN or FEAT-NNN — required for auto-close -->

---

## Type of Change

<!-- Check all that apply -->

- [ ] `feat` — New feature / story implementation
- [ ] `fix` — Bug fix
- [ ] `enabler` — Technical enabler (infra, refactor, architecture)
- [ ] `ci` — CI/CD or pipeline change
- [ ] `docs` — Documentation only
- [ ] `chore` — Dependency update / housekeeping
- [ ] `hotfix` — Urgent production fix
- [ ] `spike` — Research findings (no production code)
- [ ] ⚠️ **BREAKING CHANGE** — existing consumers must update

---

## Acceptance Criteria Checklist

> Copy from the linked Story/Feature and check off each criterion

- [ ] AC1: Given ... When ... Then ...
- [ ] AC2: Given ... When ... Then ...
<!-- Add more as needed -->

---

## Definition of Done

- [ ] Code reviewed by at least one peer
- [ ] All unit tests pass (`npm test` / `pytest` / `go test ./...`)
- [ ] Coverage ≥ 80% (lines and branches)
- [ ] Integration tests pass in CI
- [ ] No new Sev-1 / Sev-2 defects introduced
- [ ] No secrets or credentials in code
- [ ] Documentation updated (if behavior changed)
- [ ] PR title follows commit convention: `<type>(<scope>): <subject> [ARTIFACT-NNN]`
- [ ] Branch rebased on latest `main`

---

## How to Test

<!-- Step-by-step instructions for the reviewer to verify the change -->

```bash
# Example:
# 1. Start the service
npm run dev

# 2. Navigate to ...
# 3. Expect to see ...
```

---

## Screenshots / Recordings

<!-- For UI changes: attach before/after screenshots or a screen recording -->
<!-- For API changes: attach request/response examples (curl or Postman) -->
<!-- Delete this section if not applicable -->

---

## Security Checklist

<!-- Complete only if this PR touches auth, data handling, or infra -->

- [ ] Input validation applied to all external data
- [ ] No PII logged or exposed
- [ ] Auth/AuthZ applied to new endpoints
- [ ] Dependencies checked: `npm audit` / `pip-audit` / `govulncheck`
- [ ] Container image scanned (Iron Man to verify)

---

## Reviewer Notes

<!-- Anything reviewers should pay special attention to, known trade-offs, or follow-up stories planned -->



---

## Related Items

| Type | Link |
|---|---|
| Story / Feature | <!-- Link to GitHub Issue or Jira/Confluence --> |
| ADR (if applicable) | `large-solution/solution-intent/ADR-NNN-*.md` |
| Follow-up story | `STORY-NNN` <!-- if a trade-off deferred work --> |
| Postmortem (hotfix) | `continuous-delivery/devops/postmortem-INC-NNN.md` |

---

<!-- 
  Reviewer SLA:
  XS (< 50 lines):   4 hours
  S  (50-200 lines):  8 hours
  M  (200-500 lines): 24 hours
  L  (500+ lines):    48 hours — please split if possible
-->

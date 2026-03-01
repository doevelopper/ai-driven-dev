---
applyTo: "**/*.{test,spec}.{ts,tsx,js,jsx,py,go}"
---

# Testing Instructions

<!-- Loaded automatically by Copilot CLI for all test files -->

## Testing Philosophy

> "Test behavior, not implementation."
> — Write tests that survive refactoring.

## Test Pyramid

```
         ▲
        /E2E\        Few — expensive, slow, high confidence
       /──────\
      /  Integ  \    Some — test real I/O boundaries
     /────────────\
    /  Unit Tests  \  Many — fast, isolated, cheap
   /────────────────\
```

## Unit Test Rules

- **One assertion per test** (when possible)
- **AAA pattern**: Arrange → Act → Assert
- Test name describes the scenario: `<function>_<scenario>_<expected>`
  - Good: `calculateWsjf_withZeroJobSize_throwsDivisionError`
  - Bad: `test1`, `testWsjf`
- Mock external dependencies (DB, APIs, filesystem)
- No `sleep()` or time-dependent assertions

## Integration Test Rules

- Use **real** database/service instances (Docker Compose preferred)
- Test the full stack from HTTP request to persistence and back
- Clean up test data after each test (use transactions + rollback)
- Run in CI against a dedicated test environment

## BDD / Acceptance Test Rules

When writing acceptance tests, map each **Given/When/Then** from the story's acceptance criteria:

```gherkin
Feature: <Feature name from FEAT-NNN>

  Scenario: <Acceptance criterion title>
    Given <the system is in state X>
    When  <the user performs action Y>
    Then  <the system responds with Z>
```

Tools: Cucumber / Behave / Gherkin + Playwright (for UI)

## Coverage Requirements

| Type | Minimum |
|---|---|
| Line coverage | 80% |
| Branch coverage | 80% |
| Critical paths | 100% (auth, payments, data mutations) |

## Test Data Rules

- Use **factories / fixtures** — never production data
- Randomize IDs to avoid test ordering dependencies
- Store fixtures in `tests/fixtures/` or `__fixtures__/`
- No hardcoded PII (emails, phone numbers, SSNs) — use fakers

## What NOT to Test

- Third-party library internals
- Generated code (ORMs, protobuf stubs)
- Trivial getters/setters with no logic
- Configuration files

---
applyTo: "**/*.{ts,tsx,js,jsx,py,go,java,cs,rb,rs}"
---

# Coding Standards Instructions

<!-- Loaded automatically by Copilot CLI for all code files -->

## General Principles

- **Readability first**: code is read 10× more than it is written
- **SOLID principles**: single responsibility, open/closed, Liskov, interface segregation, dependency inversion
- **DRY**: extract reusable logic; avoid copy-paste
- **YAGNI**: don't build what isn't needed yet

## Naming

| Element | Convention | Example |
|---|---|---|
| Variables | camelCase (JS/TS) / snake_case (Python) | `userCount`, `user_count` |
| Functions | verb + noun | `fetchUserById`, `calculateWsjf` |
| Classes | PascalCase | `EpicOwner`, `ReleaseTrain` |
| Constants | UPPER_SNAKE | `MAX_WIP_LIMIT` |
| Files | kebab-case | `epic-owner-service.ts` |

## Functions

- Max **30 lines** per function
- Max **3 parameters** (use object/struct for more)
- Return early to avoid deep nesting
- Pure functions preferred (no side effects)

## Error Handling

- **Never swallow errors silently** — log or rethrow
- Use typed errors / custom exception classes
- Distinguish user errors (4xx) from system errors (5xx) in APIs

## Testing Requirements

Every function must have:
- Unit test covering the happy path
- Unit test covering at least one edge/error case
- Integration test if it touches I/O (database, API, filesystem)

Minimum coverage: **80%** lines and branches.

## Documentation

- Public functions: JSDoc / docstring with `@param` and `@returns`
- Complex algorithms: inline comment explaining *why*, not *what*
- No TODO comments in production code — create a story instead

## Security Checklist (per PR)

- [ ] No secrets in code
- [ ] Input validation on all external data
- [ ] SQL parameters use prepared statements
- [ ] Dependencies checked for known CVEs
- [ ] Auth/AuthZ applied to all endpoints

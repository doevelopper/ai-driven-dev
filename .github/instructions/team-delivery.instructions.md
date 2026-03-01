---
applyTo: "teams/**/*.md"
---

# Team Delivery Instructions

<!-- Loaded automatically by Copilot CLI when working in teams/ -->

## Active Agent Persona

**Think like Hermione (Product Owner)** when writing stories, acceptance criteria, or iteration goals.
**Think like Spider-Man (Scrum Master)** when facilitating ceremonies or coaching practices.
**Think like Wolverine (Senior Dev)** when generating, reviewing, or refactoring code.
**Think like Iron Man (DevOps)** when touching pipelines, infrastructure, or deployment scripts.

## Story Writing Rules (Hermione mode)

Every story must have:

```markdown
## User Story
As a <specific user role>,
I want <concrete action or goal>,
So that <business or user value>.

## Acceptance Criteria
- Given <context>, When <action>, Then <expected outcome>
- Given <context>, When <edge case>, Then <correct handling>

## Definition of Done
- [ ] Code reviewed by at least one peer
- [ ] Unit tests passing (coverage ≥ 80%)
- [ ] Integration tests passing in CI
- [ ] No Sev-1/Sev-2 defects open
- [ ] Accepted by Product Owner
- [ ] Documentation updated (if applicable)
```

### Story Sizing Rules
| Points | Meaning |
|---|---|
| 1 | Trivially simple, < 2 hours |
| 2 | Simple, < half a day |
| 3 | Straightforward, ~1 day |
| 5 | Moderate complexity, 2–3 days |
| 8 | Complex, nearly a full iteration — consider splitting |
| 13+ | Too large — **must split** |

A story > 8 points must be split before being placed in an iteration.

## Story Splitting Patterns

When asked to split a story, use these patterns (in order of preference):

1. **By workflow step**: split along sequential steps in the user journey
2. **By data variation**: one story per key data type or scenario
3. **By interface**: back-end first, then front-end as a separate story
4. **By happy/sad path**: happy path first; error/edge cases in follow-up stories
5. **By role**: split by user type if multiple personas are served

## Iteration Goal Format

```markdown
## Iteration NN Goals

1. Deliver <Feature/Epic context>: complete STORY-XXX, STORY-YYY
2. Resolve tech debt: STORY-ZZZ (enabler)
3. Stretch: STORY-WWW (if capacity allows)
```

## Backlog Health Checklist

Run this before every Iteration Planning:
- [ ] 2–3 iterations of groomed, ready stories available
- [ ] All "Ready" stories have complete acceptance criteria
- [ ] No story > 8 points in the "Ready" state
- [ ] Stories are linked to a Feature (`FEAT-NNN`)
- [ ] Top stories are aligned with PI Objectives

## Retrospective Action Item Rules (Spider-Man mode)

- Max **3 action items** per iteration (quality over quantity)
- Every action item has: Owner + Due date (next iteration)
- Track in iteration file under `## Retrospective Notes > Action Items`
- Open action items reviewed first in next retrospective

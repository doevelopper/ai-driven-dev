# Prompt: Write an Incident Postmortem

**Persona:** Iron Man (DevOps / Platform Engineer)
**Level:** ART / DevOps
**Output:** `continuous-delivery/devops/postmortem-INC-NNN.md`

---

## Instructions

<!-- AI: You are Iron Man, DevOps Engineer. Write a blameless postmortem following the standard structure. Focus on systemic causes, not individual failures. Generate actionable improvement stories. -->

Act as **Iron Man (DevOps)**. Write a blameless postmortem for:

**Incident ID:** `[INC-NNN]`

**Severity:** `[Sev-1 / Sev-2]`

**Date:** `[YYYY-MM-DD]`

**Duration:** `[N hours N minutes]`

**Impact summary:**
```
[WHO WAS AFFECTED, HOW MANY USERS, WHAT FUNCTIONALITY WAS DOWN]
```

**Timeline of events:**
```
[HH:MM UTC — Event description]
[HH:MM UTC — Event description]
...
```

**What was done to restore service:**
```
[DESCRIBE THE REMEDIATION STEPS]
```

(optional: On-call engineer: [NAME])
(optional: Monitoring/alert that triggered (or didn't): [DESCRIBE])

---

## Expected Output

```markdown
# Postmortem — INC-NNN

**Date:** YYYY-MM-DD
**Severity:** Sev-X
**Duration:** N hours N minutes
**Status:** Draft / Reviewed / Final
**Author:** Iron Man (DevOps)

---

## Impact

<Who, what, and how severely were users affected>

---

## Timeline

| Time (UTC) | Event |
|---|---|
| HH:MM | <Event> |
| HH:MM | <Mitigation action> |
| HH:MM | <Service restored> |

---

## Root Cause

<One clear sentence stating the root cause>

### Contributing Factors

1. <Factor 1>
2. <Factor 2>

### 5-Whys Analysis

Why 1: ...
Why 2: ...
Root cause: ...

---

## Detection

**How was the incident detected?** <Alert / Customer report / Manual>
**Time to detect:** N minutes
**Improvement needed?** Yes/No — <describe>

---

## Response

**Time to acknowledge:** N minutes
**Time to mitigate:** N minutes
**Time to resolve:** N minutes

---

## Action Items

| # | Action | Type | Owner | Due | Story |
|---|---|---|---|---|---|
| 1 | <Prevention action> | Monitoring/Code/Process | Iron Man | <date> | STORY-NNN |

---

## Lessons Learned

- <Key insight 1>
- <Key insight 2>

---

## Blameless Statement

> This postmortem focuses on systems and processes, not individuals.
> All engineers acted in good faith with the information available at the time.
```

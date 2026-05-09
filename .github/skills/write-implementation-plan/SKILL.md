---
name: write-implementation-plan
description: Produce a concise implementation plan for multi-step SQL Server, Flyway, SSIS, or Azure DevOps work before editing files.
---

# Write Implementation Plan

Use when the task requires more than one small edit.

The plan must be clear enough for another engineer to execute.

## Plan format

```text
Goal:
Scope:
Files/objects to inspect:
Files/objects to change:
Implementation steps:
Validation steps:
Deployment path:
Risks and recovery notes:
```

## Rules

- Use exact file paths when known.
- Do not include placeholders like `TBD`.
- Do not invent environment names, variable groups, or secrets.
- Keep tasks small and reviewable.
- Include DEV, ENT, and QA implications when deployment is involved.

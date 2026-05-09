---
name: ssis-change-workflow
description: Workflow for analyzing and changing SSIS packages, projects, parameters, connection managers, and orchestration dependencies.
---

# SSIS Change Workflow

Use for SSIS package or orchestration changes.

## Procedure

1. Identify the package/project impacted.
2. Identify connection managers, parameters, variables, and expressions.
3. Identify Execute SQL Tasks and Data Flow Tasks involved.
4. Identify source and destination tables.
5. Check package execution order and parent/child dependencies.
6. Check deployment model and environment parameters if represented in repo.
7. Design the smallest package or SQL change.
8. Provide DEV validation steps and ENT/QA promotion notes.

## Safety rules

- Do not hardcode connection strings.
- Do not rename SSIS assets without dependency analysis.
- Preserve logging and failure behavior.
- Avoid changing package execution order unless specifically required.

## Output

```text
Package impact:
SQL impact:
Parameters/connections impacted:
Validation steps:
Deployment notes:
Recovery/rerun notes:
```

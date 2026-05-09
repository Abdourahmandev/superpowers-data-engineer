---
name: using-data-engineering-superpowers
description: Bootstrap workflow for local Copilot data engineering tasks. Use at the start of SQL Server, Flyway, SSIS, Azure DevOps, debugging, planning, or release-safety work.
---

# Using Data Engineering Superpowers

Use this skill before starting a non-trivial task in this repository.

## First move

Classify the request:

1. SQL Server object change.
2. Flyway migration.
3. SSIS orchestration/package change.
4. Azure DevOps pipeline change.
5. Debugging or performance issue.
6. Release readiness review.
7. Documentation only.

Then select the right workflow skill:

- `sql-change-workflow`
- `flyway-migration-workflow`
- `ssis-change-workflow`
- `azure-devops-pipeline-workflow`
- `root-cause-debugging`
- `deployment-readiness-check`
- `code-review`

## Working rule

Do not jump straight into code. First state the short plan unless the user explicitly asks for a tiny edit.

Use this output shape:

```text
Task type:
Impacted area:
Plan:
Validation:
Risk:
```

## Stop conditions

Stop and ask or state uncertainty when:

- A server, database, variable group, or secret name is missing.
- The change could delete, truncate, overwrite, or corrupt data.
- A migration appears already applied.
- SSIS package dependencies are unclear.
- Pipeline logs are missing for a debugging request.

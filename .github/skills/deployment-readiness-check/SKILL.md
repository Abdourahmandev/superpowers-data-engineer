---
name: deployment-readiness-check
description: Pre-release checklist for SQL Server, Flyway, SSIS, and Azure DevOps changes before DEV, ENT, and QA promotion.
---

# Deployment Readiness Check

Use before saying a database or pipeline change is ready.

## Checklist

### Scope

- What files changed?
- What SQL objects changed?
- What SSIS packages changed?
- What pipeline stages changed?

### Safety

- Any data loss risk?
- Any breaking schema change?
- Any already-applied migration edited?
- Any secrets or environment-specific values committed?
- Any missing variable group/service connection assumptions?

### Validation

- DEV validation command/query/package run.
- ENT validation plan.
- QA validation plan.
- Flyway `info` / `validate` / `migrate` plan or evidence.
- SQL regression query.
- SSIS package validation, if impacted.

### Recovery

- Rollback strategy or forward-fix strategy.
- Rerun instructions.
- Data correction strategy if data was modified.

## Output

```text
Decision: Ready / Not ready / Ready with conditions
Scope:
Validation evidence:
Validation still required:
Risks:
Recovery notes:
```

Do not mark as Ready without evidence.

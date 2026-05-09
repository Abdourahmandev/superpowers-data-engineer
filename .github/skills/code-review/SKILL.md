---
name: code-review
description: Review SQL Server, Flyway, SSIS, and Azure DevOps changes for correctness, safety, and deployment readiness.
---

# Code Review

Use when reviewing a diff, PR, migration, pipeline, SQL script, or SSIS-related change.

## Review dimensions

- Correctness.
- Data safety.
- Migration safety.
- Environment safety.
- Security/secrets.
- Performance.
- SSIS orchestration impact.
- Azure DevOps deployment impact.
- Validation evidence.

## Severity

Blocker:

- Data loss risk without approval.
- Secrets in files.
- Already-applied Flyway migration modified.
- Likely deployment failure.
- Missing validation for critical change.

Major:

- Missing dependency analysis.
- Unclear rollback/recovery.
- Likely performance regression.
- Hard-to-review large change.

Minor:

- Style, comments, naming, or documentation improvements.

## Output format

```text
Decision: Approve / Approve with comments / Block
Blockers:
Major issues:
Minor issues:
Validation gaps:
Suggested next step:
```

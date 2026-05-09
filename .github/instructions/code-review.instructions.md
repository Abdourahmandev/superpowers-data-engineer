---
applyTo: "**"
---

# Code Review Instructions

When reviewing data engineering changes, classify issues by severity.

## Blocker

A blocker prevents merge or deployment:

- Data loss risk without approval.
- Secrets committed to files.
- Flyway migration likely to fail or already-applied migration modified.
- Environment-specific hardcoding.
- SQL syntax likely invalid.
- Missing validation for critical database change.
- SSIS package dependency broken.

## Major

A major issue should be fixed before deployment:

- Missing dependency analysis.
- Missing rollback/recovery notes for risky migration.
- Performance concern with likely production impact.
- Pipeline variable or artifact assumption not verified.
- Naming convention inconsistency.

## Minor

A minor issue improves maintainability:

- Formatting inconsistency.
- Unclear comments.
- Missing optional documentation.
- Redundant SQL.

## Review output format

Use:

```text
Decision: Approve / Approve with comments / Block
Blockers:
Major issues:
Minor issues:
Validation gaps:
Suggested next step:
```

---
applyTo: "**/*.sql"
---

# SQL Server Instructions

Use these rules for `.sql` files.

## Style

- Use explicit schema names.
- Use clear aliases and readable formatting.
- Prefer deterministic ordering in validation queries.
- Avoid `SELECT *` in persistent objects.
- Use `CREATE OR ALTER` for procedures, functions, and views when compatible with the repository pattern.
- Keep transaction scope explicit for data changes.
- Use `SET XACT_ABORT ON` for multi-step transactional scripts when appropriate.

## Safety

- Do not drop, truncate, rename, or mass-update data without explicit approval.
- For schema changes, consider dependencies: views, procedures, SSIS packages, downstream reports, and Flyway order.
- For nullable/non-nullable changes, state data backfill requirements.
- For index changes, explain write overhead and maintenance impact.

## Validation

For each SQL change, provide at least one of:

- Syntax validation command or mssql execution instruction.
- Dependency check query.
- Row count reconciliation query.
- Before/after performance observation.
- Regression query for affected business logic.

## Preferred verification snippets

```sql
-- Confirm object exists
SELECT s.name AS schema_name, o.name AS object_name, o.type_desc
FROM sys.objects o
JOIN sys.schemas s ON s.schema_id = o.schema_id
WHERE s.name = 'dbo'
  AND o.name = '<object_name>';
```

```sql
-- Find dependencies by referenced object name
SELECT
    OBJECT_SCHEMA_NAME(referencing_id) AS referencing_schema,
    OBJECT_NAME(referencing_id) AS referencing_object,
    referenced_schema_name,
    referenced_entity_name
FROM sys.sql_expression_dependencies
WHERE referenced_entity_name = '<object_name>'
   OR OBJECT_NAME(referencing_id) = '<object_name>';
```

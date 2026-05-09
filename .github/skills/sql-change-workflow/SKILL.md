---
name: sql-change-workflow
description: Workflow for changing SQL Server tables, views, procedures, functions, indexes, or data safely.
---

# SQL Change Workflow

Use for SQL Server object or data changes.

## Procedure

1. Inspect existing object definitions and naming patterns.
2. Identify dependencies using repository search and SQL dependency queries where possible.
3. Decide if the change requires Flyway.
4. Design the smallest safe SQL change.
5. Avoid destructive changes unless explicitly approved.
6. Add validation SQL.
7. State deployment and recovery notes.

## Dependency checks

Use repository search for object names in:

- SQL files.
- SSIS packages or project files.
- Pipeline scripts.
- Documentation.

Suggested SQL dependency query:

```sql
SELECT
    OBJECT_SCHEMA_NAME(referencing_id) AS referencing_schema,
    OBJECT_NAME(referencing_id) AS referencing_object,
    referenced_schema_name,
    referenced_entity_name
FROM sys.sql_expression_dependencies
WHERE referenced_entity_name = '<object_name>'
   OR OBJECT_NAME(referencing_id) = '<object_name>';
```

## Output after implementation

```text
Changed files:
Changed SQL objects:
Validation performed:
Validation still required:
Deployment impact:
Recovery notes:
```

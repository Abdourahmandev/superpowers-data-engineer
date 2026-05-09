---
applyTo: "**/*.{sql,conf,yml,yaml,ps1,sh}"
---

# Flyway Instructions

Use these rules when the task involves Flyway migrations or deployment.

## Migration naming

Use:

```text
VYYYYMMDD_NNN__short_description.sql
R__short_description.sql
```

Examples:

```text
V20260509_001__create_customer_dimension.sql
V20260509_002__alter_fact_sales_add_column.sql
R__refresh_reporting_views.sql
```

## Versioned migrations

- Create a new versioned migration for schema or data changes.
- Do not modify an already-applied migration unless the user confirms it has not been applied anywhere.
- Keep each migration focused on one logical change.
- Avoid environment-specific SQL in migration files.
- Avoid references to local mssql profiles inside migration files.

## Repeatable migrations

Use repeatable migrations only for objects intended to be recreated or refreshed, such as:

- Views.
- Functions.
- Stable stored procedures where the team pattern allows it.

## Safety checklist

Before finalizing a migration, state:

- Whether it is versioned or repeatable.
- Whether it is safe to run more than once.
- Whether it changes data, schema, or both.
- Whether it has downstream SSIS/reporting impact.
- How to verify after migration.
- How to recover if deployment fails.

## Validation commands

Use the project’s existing Flyway commands if present. If not present, suggest generic commands without embedding secrets:

```bash
flyway info
flyway validate
flyway migrate
flyway info
```

For Azure DevOps, do not invent variable names. Inspect the YAML first and reuse existing variable/group patterns.

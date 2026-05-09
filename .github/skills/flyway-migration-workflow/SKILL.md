---
name: flyway-migration-workflow
description: Workflow for creating or reviewing Flyway migrations for SQL Server with DEV, ENT, and QA promotion.
---

# Flyway Migration Workflow

Use for schema/data changes delivered through Flyway.

## Naming

Versioned migration:

```text
VYYYYMMDD_NNN__short_description.sql
```

Repeatable migration:

```text
R__short_description.sql
```

## Procedure

1. Locate existing migration folder.
2. Inspect latest migration version for naming and sequence.
3. Decide versioned vs repeatable.
4. Create a focused migration file.
5. Avoid environment-specific SQL.
6. Add comments only where they clarify risk or business logic.
7. Add verification SQL in the response or in a companion doc if the repo has that pattern.
8. State recovery notes.

## Review checklist

- New migration, not edited historical migration.
- Naming convention followed.
- Object names schema-qualified.
- No hardcoded secrets or environment values.
- Data update has WHERE clause and row-count expectation where possible.
- Repeatable migration is appropriate.
- Validation commands listed.

## Validation commands

Use existing project commands if available. Otherwise suggest:

```bash
flyway info
flyway validate
flyway migrate
flyway info
```

Do not claim these passed unless they were actually run and output was reviewed.

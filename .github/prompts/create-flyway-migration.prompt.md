---
name: create-flyway-migration
description: Create or plan a Flyway migration using the repository convention.
agent: 'Flyway Migration Agent'
argument-hint: '[schema/data change description]'
---

Create or plan the Flyway migration for this change.

Follow:

```text
VYYYYMMDD_NNN__short_description.sql
R__short_description.sql
```

Before editing, inspect existing migrations and determine the next sequence number for today.

Output changed files, validation commands, and recovery notes.

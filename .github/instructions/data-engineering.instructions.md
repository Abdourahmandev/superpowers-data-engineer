---
applyTo: "**"
---

# Data Engineering Workplace Instructions

Apply these rules to all work in this repository.

## Working assumptions

- This repository supports SQL Server data engineering work.
- SQL Server access happens through VS Code mssql extension profiles.
- Environments are DEV, ENT, and QA.
- CI/CD is handled in Azure DevOps.
- Database delivery uses Flyway.
- Orchestration uses SSIS.

## Mandatory thinking pattern

Before editing files, identify:

- The data object or orchestration component being changed.
- The environment where the change should first be validated.
- Whether a Flyway migration is required.
- Whether SSIS or Azure DevOps is impacted.
- What proves the change works.

## Safety rules

- Never commit secrets.
- Never invent connection details.
- Never make destructive data changes without explicit approval.
- Prefer forward-only changes and clear recovery notes.
- Preserve existing naming conventions and folder structure.
- Keep changes small enough for code review.

## Definition of done

A task is not done until the response includes:

- Files changed.
- SQL objects or packages impacted.
- Validation performed or validation still required.
- Deployment impact across DEV, ENT, and QA.
- Known risks or rollback/recovery notes.

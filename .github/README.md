# Data Engineering Copilot Superpowers

Local GitHub Copilot customizations for a SQL Server data engineering workplace using VS Code, the mssql extension, Flyway, Azure DevOps, and SSIS.

This package adapts the Superpowers idea into local Copilot primitives:

- `.github/copilot-instructions.md` for always-on behavior.
- `.github/instructions/*.instructions.md` for file/path-specific rules.
- `.github/agents/*.agent.md` for specialized local agents.
- `.github/skills/*/SKILL.md` for reusable workflows.
- `.github/prompts/*.prompt.md` for slash-command style tasks.

## Install

Copy the `.github` folder to the root of your repository.

Then open the repository in VS Code with GitHub Copilot enabled. In Copilot Chat, use Agent mode and run:

```text
/skills
/agents
```

Use the diagnostics view if Copilot does not load the files: right-click inside Copilot Chat and select **Diagnostics**.

## Recommended workflow

For any data engineering task, follow:

```text
Understand → Plan → Implement → Validate → Review → Summarize
```

For risky database changes, add:

```text
Impact analysis → Migration safety → Rollback/recovery notes → DEV → ENT → QA validation
```

## Important assumptions

- Connection details for DEV, ENT, and QA already live in the VS Code mssql extension.
- No server names, passwords, connection strings, tokens, or secrets should be committed.
- Flyway migration naming convention is:

```text
VYYYYMMDD_NNN__short_description.sql
R__short_description.sql
```

Example:

```text
V20260509_001__create_customer_dimension.sql
V20260509_002__alter_fact_sales_add_column.sql
R__refresh_reporting_views.sql
```

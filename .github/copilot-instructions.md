# Repository Copilot Instructions: Data Engineering Superpowers

You are assisting in a professional data engineering repository.

The stack is:

- GitHub Copilot in VS Code.
- SQL Server through the VS Code mssql extension.
- Three database environments: DEV, ENT, and QA.
- Azure DevOps for CI/CD.
- Flyway for database migrations.
- SSIS for orchestration.

## Non-negotiable operating mode

Before proposing code or editing files, classify the request:

1. SQL Server object change: table, view, procedure, function, index, permission, seed/reference data.
2. Flyway migration change.
3. SSIS orchestration/package/job change.
4. Azure DevOps pipeline or release change.
5. Debugging/performance issue.
6. Release/deployment readiness check.
7. Documentation or analysis only.

Then use the most relevant local skill from `.github/skills` and the most relevant instructions from `.github/instructions`.

Do not jump directly to implementation unless the request is tiny and safe.

## Default workflow

Use this sequence for all non-trivial work:

1. Understand the request and impacted systems.
2. Inspect existing patterns before inventing a new one.
3. Produce a short implementation plan.
4. Make the smallest safe change.
5. Validate with concrete commands, queries, or manual verification steps.
6. Review for release risk.
7. Summarize exactly what changed and what remains unverified.

## Environment rules

- DEV is the first implementation and developer-validation environment.
- ENT is an integration / enterprise validation environment.
- QA is the quality assurance validation environment.
- Never hardcode environment connection details.
- Never write credentials, connection strings, tokens, or server names into repository files.
- Use existing VS Code mssql extension profiles or project-level non-secret references.
- If environment details are missing, ask for them instead of guessing.

## SQL Server rules

- Prefer explicit schema names, for example `dbo.Customer` rather than `Customer`.
- Avoid destructive statements unless the user explicitly approves them.
- For potentially destructive changes, include impact analysis and recovery notes.
- Check dependencies before altering tables, views, stored procedures, functions, indexes, or columns.
- For performance work, identify the observed symptom, query pattern, cardinality assumptions, indexes, and execution plan considerations before proposing changes.
- Do not use `SELECT *` in production SQL objects unless the existing codebase pattern requires it and the reason is documented.
- Avoid `NOLOCK` unless the business accepts dirty reads and the reason is documented.

## Flyway rules

- Create new versioned migrations. Do not edit applied versioned migrations unless explicitly told this is a local/unapplied migration.
- Use naming convention: `VYYYYMMDD_NNN__short_description.sql`.
- Use repeatable migrations only for objects that are intended to be reapplied, such as stable views or functions.
- Make migrations forward-only unless the repository has a formal undo strategy.
- Include verification SQL or manual validation notes when creating migrations.

## SSIS rules

- Treat SSIS changes as orchestration changes with downstream impact.
- Identify impacted package, connection manager, parameter, SQL task, data flow, and job schedule where applicable.
- Do not rename package parameters, variables, or connection managers without impact analysis.
- Include operational checks: package execution order, retry/failure behavior, logging, and environment-specific parameters.

## Azure DevOps rules

- Keep pipeline changes small and reviewable.
- Do not introduce secrets into YAML.
- Prefer variables/groups/service connections already managed outside the repo.
- For Flyway deployment stages, make environment promotion explicit: DEV → ENT → QA.
- Include validation commands or pipeline checks before claiming the pipeline is fixed.

## Verification rule

Never claim a change is complete, fixed, deployed, safe, or passing without fresh verification evidence.

If you could not run the verification, say exactly what remains unverified and give the user the command or manual check to run.

## Response style

- Be concise.
- Be practical.
- Prefer checklists for plans and release readiness.
- Avoid long theory unless asked.
- When uncertain, state the uncertainty clearly and propose the safest next check.

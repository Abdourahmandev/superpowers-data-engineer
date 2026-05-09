---
applyTo: "**/*.{dtsx,dtproj,conmgr,params,ispac,sql,md}"
---

# SSIS Instructions

Use these rules for SSIS-related work.

## Impact analysis

Before changing SSIS artifacts, identify:

- Package name.
- Project name.
- Connection managers.
- Parameters and variables.
- Execute SQL Tasks.
- Data Flow Tasks.
- Source and destination tables.
- Precedence constraints.
- Parent/child package dependencies.
- SQL Server Agent job or schedule, if applicable.

## Safety rules

- Do not rename parameters, variables, packages, or connection managers without impact analysis.
- Do not hardcode environment-specific connection strings.
- Preserve package logging and error handling patterns.
- Preserve existing transaction and retry semantics unless the user asks to change them.

## Validation

For each SSIS change, provide:

- Package-level validation steps.
- Execution order impact.
- DEV execution recommendation.
- ENT and QA promotion notes.
- Any needed SQL validation queries.

## Documentation

When SSIS behavior changes, document:

- What package changed.
- Why it changed.
- What data movement is affected.
- How failure is detected.
- How the operator should rerun or recover.

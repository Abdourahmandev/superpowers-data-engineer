---
applyTo: "**/*.{yml,yaml,ps1,sh,cmd,bash,json}"
---

# Azure DevOps CI/CD Instructions

Use these rules for Azure DevOps pipeline and deployment work.

## Pipeline safety

- Inspect existing YAML patterns before editing.
- Do not invent service connections, variable groups, secure files, or secret names.
- Keep stages explicit and environment-aware.
- Avoid mixing build, validation, migration, and release concerns in one unclear step.
- Prefer small, readable scripts over large inline commands.

## Flyway deployment flow

Unless the repository says otherwise, use this promotion logic:

```text
Build/Validate → DEV migration → ENT migration → QA migration
```

Each environment should have clear gates, approvals, or manual validation points according to the existing pipeline pattern.

## Required checks

For any pipeline change, include:

- What stage/job/step changed.
- What variables or artifacts are consumed.
- Whether secrets are required and where they should live outside the repo.
- How to validate the pipeline.
- What failure mode the change addresses.

## Debugging rule

For failing pipelines, do not guess. Read the failing task log, identify the exact command, exit code, file path, and environment variable assumptions before proposing fixes.

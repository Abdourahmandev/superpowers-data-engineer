---
name: azure-devops-pipeline-workflow
description: Workflow for Azure DevOps YAML, CI/CD, Flyway deployment, and pipeline debugging tasks.
---

# Azure DevOps Pipeline Workflow

Use for Azure DevOps pipeline work.

## Procedure

1. Inspect existing YAML and scripts.
2. Identify pipeline trigger, stages, jobs, tasks, artifacts, and variables.
3. For failures, read the exact failing command, error, and exit code.
4. Reuse existing variable groups and service connection patterns.
5. Keep changes small.
6. Keep secrets outside the repo.
7. Make DEV → ENT → QA promotion explicit if touching deployment.
8. Provide validation steps.

## Debugging pipeline failures

Do not guess. Capture:

```text
Failed stage/job/step:
Exact command:
Exit code:
Relevant log lines:
Recent change:
Hypothesis:
Minimal test/fix:
```

## Review checklist

- YAML syntax is likely valid.
- Paths match repository structure.
- Artifact names match producer/consumer stages.
- Variables are existing or clearly marked as required external config.
- No secrets committed.
- Flyway commands align with the repo pattern.

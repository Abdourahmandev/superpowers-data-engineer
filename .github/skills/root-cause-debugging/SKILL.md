---
name: root-cause-debugging
description: Systematic debugging workflow for SQL failures, Flyway errors, SSIS package failures, Azure DevOps failures, and performance issues.
---

# Root Cause Debugging

Use for any bug, build failure, deployment failure, SQL error, SSIS failure, or performance issue.

## Rule

No fix before root cause.

## Phase 1: Gather evidence

Capture:

- Exact error message.
- Failing command/query/package/task.
- Environment: DEV, ENT, or QA.
- Last known working state.
- Recent changes.
- Logs or execution output.

## Phase 2: Reproduce or isolate

Identify whether the issue is:

- SQL syntax/runtime error.
- Missing object or permission.
- Data quality issue.
- Flyway checksum/order/config issue.
- SSIS connection/parameter/package issue.
- Azure DevOps artifact/variable/agent issue.
- Performance regression.

## Phase 3: Form one hypothesis

Use:

```text
I think the root cause is <specific cause> because <evidence>.
```

Test one thing at a time.

## Phase 4: Fix and verify

- Apply the smallest fix.
- Run the verification command/query/package step.
- If verification cannot be run, state exactly what the user should run.

## Stop condition

After three failed fixes, stop and question the architecture or assumptions instead of stacking more patches.

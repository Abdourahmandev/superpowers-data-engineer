---
name: analyze-request
description: Classify a data engineering request before planning or implementing SQL Server, Flyway, SSIS, or Azure DevOps changes.
---

# Analyze Request

Use this skill before planning or editing.

Answer these questions:

1. What is the user asking for?
2. Which technology is impacted: SQL Server, Flyway, SSIS, Azure DevOps, or docs?
3. Is this a schema change, data change, orchestration change, deployment change, debugging task, or review task?
4. Which environment is involved first: DEV, ENT, or QA?
5. What files or objects likely need inspection?
6. What could go wrong?
7. What proves success?

Output:

```text
Request summary:
Task type:
Impacted technologies:
Likely files/objects:
Assumptions:
Risks:
Next step:
```

Keep it short.

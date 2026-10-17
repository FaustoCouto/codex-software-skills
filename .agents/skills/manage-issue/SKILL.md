---
name: manage-issue
description: Select eligible work from the confirmed tracker for explicitly scoped workspace projects.
---

# Product Owner

Read [the project scope contract](../references/project-scope.md) first and
validate `project_ids` from the user's request. Never infer projects from the
current directory or from a project kind.

For each requested project, or the supplied `target_project_id` when the
coordinator has narrowed this subtask:

1. Read that project's `AGENTS.md`, tracker details, and
   `workflow_files.role_skills.manage_issue` and `workflow_files.issue_protocol`
   when present.
2. If the tracker or role procedure is unknown, ask for the missing
   project-specific information. Do not assume GitHub Issues or reuse another
   project's process.
3. Follow that project's issue eligibility, reservation, and reporting rules.
   Select at most one eligible work item for each target project and do not
   edit code or perform delivery Git operations.

Report each selected work item with its project ID, repository path, issue
reference, acceptance criteria, dependencies, and reservation status. When
handing the result to the Scrum Master or another skill, state the original
`project_ids=[...]` unchanged and include the exact `target_project_id`.

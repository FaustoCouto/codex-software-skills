---
name: implement-issue
description: Implement one assigned work item in the selected project's own Git repository.
---

# Software Developer

Read [the project scope contract](../references/project-scope.md) first and
validate `project_ids`. This skill requires exactly one valid
`target_project_id`. If it is missing or ambiguous, ask the coordinator which
requested project owns the work item; do not choose based on the issue, current
directory, or project type.

Read the target project's nearest `AGENTS.md`, the assigned work item's
acceptance criteria, and the relevant `workflow_files`, including
`role_skills.implement_issue`, `task_setup`, and `issue_protocol` when present.
Confirm that the target path is that project's own Git repository and follow
its branch and worktree procedure. Never use the workspace configuration
repository as a code repository. If the repository or required procedure is
missing, stop and ask for it; do not create or move project files to compensate.

Implement only the assigned criteria in the target project. Preserve local
changes and follow its constants, architecture, test, and security rules. Run
only validation commands confirmed for that project, from its repository root.
Do not commit, push, merge, or create or update a pull request.

At handoff, report the target project ID, repository and worktree, changed
files, validation commands and results, and unresolved issues. Call QA or the
coordinator with the unchanged original `project_ids=[...]` and the exact
`target_project_id`.

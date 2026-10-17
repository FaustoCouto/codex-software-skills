---
name: qa-issue
description: Review an assigned project's changes against its acceptance criteria without editing project files.
---

# Quality Assurance

Read [the project scope contract](../references/project-scope.md) first and
validate `project_ids`. For a project-specific review, require a valid
`target_project_id`; if several projects are in scope and the target is
missing or ambiguous, ask rather than choosing one.

Read the target project's nearest `AGENTS.md`, the assigned work item's
acceptance criteria, the change diff, and the relevant files in
`workflow_files` (including `role_skills.qa_issue` and `issue_protocol` when
present). Follow any project-specific review-session or evidence-reporting
requirements. Review behavior, security, architecture, validation, tests, and
regressions as applicable. Do not modify project files, branches, issue state,
or pull requests.

Run only validation commands confirmed for the target project, from its own
repository root. Report findings by severity with file references and
reproduction evidence, then give the result to the coordinator. Every handoff
must include the unchanged original `project_ids=[...]` and the exact
`target_project_id`.

---
name: run-harness
description: Coordinate scoped project work, preserve handoff scope, and verify project and integration results.
---

# Scrum Master

Read [the project scope contract](../references/project-scope.md) first.
Validate `project_ids` against the root `workspace.yaml` before planning. If
the list is missing, invalid, or ambiguous, ask which exact project IDs to
include; never infer scope. Preserve the original list for every handoff.

For a multi-project task, maintain a task register containing the original
`project_ids`, each `target_project_id`, subtask, owner or skill, repository
path, issue/reference, confirmed validation commands and outcomes, and the
combined integration procedure and outcome. Resolve project-specific rules
from each project's own `AGENTS.md` and `workflow_files`; do not transfer API
commands, remotes, issue procedures, or branch rules to another project.

Delegate each project-specific subtask with both the full unchanged list and
its target, for example:

```text
$manage-issue project_ids=[faustocouto-open-delivery-api,open-delivery-front] target_project_id=faustocouto-open-delivery-api
```

This example uses IDs currently in the manifest. Use exact manifest IDs in
real handoffs. Do not reduce the `project_ids` list to the target or add
projects. If a project lacks a repository, tracker, workflow, or required
validation procedure, ask for the missing information and keep that subtask
unresolved.

Coordinate discovery, issue selection, implementation, and read-only QA only
where the project's confirmed procedures support those steps. Keep a separate
record for every subtask and project target. For code work, verify each change
and Git operation stays inside that project's own repository and worktree.

A multi-project task is complete only when every selected project's applicable
confirmed validations and the confirmed combined integration validation have
passed. Missing or unspecified validation is not a pass. Stop at human review;
do not commit, push, merge, or create or update pull requests unless separately
authorized.

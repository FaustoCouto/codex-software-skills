# Project scope and handoffs

## Validate the requested projects

Every invocation of a workspace skill must include `project_ids=[...]`. Treat
the values as exact `project_id` strings from the root `workspace.yaml`, not as
categories, directory names, or inferred aliases.

Before acting:

1. Read `workspace.yaml` and resolve every requested ID to exactly one entry.
2. If the list is missing, empty, duplicated, contains an unknown ID, or cannot
   be resolved unambiguously, stop and ask which manifest project IDs to use.
3. Preserve the input list and its order for the whole task. Do not add,
   remove, or replace IDs based on the current directory, project kind, issue,
   or assumptions.
4. If `target_project_id` is supplied, verify it is exactly one member of the
   original `project_ids`. A project-specific subtask must carry both values.

Do not begin project work until this validation succeeds. Example handoff:

```text
$qa-issue project_ids=[faustocouto-open-delivery-api,open-delivery-front] target_project_id=faustocouto-open-delivery-api
```

This example uses IDs currently present in `workspace.yaml`; use the exact
values from that file in each real handoff.

## Resolve project-specific instructions

Resolve each manifest `path` relative to the workspace root. For a selected
project, read its nearest `AGENTS.md` and the relevant files named in that
project's `workflow_files` before applying its procedures. Workflow paths are
relative to that project's root.

Treat null or absent fields as unknown. Do not invent a remote, issue tracker,
repository, branch base, command, or project procedure. If the requested role
needs information the manifest and project instructions do not provide, ask
for it before taking the dependent action. A directory without its own Git
repository is not a code repository; do not create a repository or move files
to make it one.

## Keep project work isolated

For code changes, use the selected project's own Git repository, branch, and
worktree. Run Git commands from that repository or explicitly against its path;
never use the workspace configuration repository as a code repository. Use
only validation commands recorded for the selected project or confirmed in
its own instructions, and run them in that project's root.

## Handoff contract

Every call to another skill, agent, or coordinator must state the unchanged
original list explicitly as `project_ids=[...]`. If the work is for one
project, include `target_project_id=<exact-id>` as well. Never pass only the
target ID in place of the original list. If the target or next step is
ambiguous, ask rather than silently choosing or widening scope.

## Multi-project completion

The Scrum Master keeps a task register with at least the original
`project_ids`, each `target_project_id`, subtask and owner, project repository,
confirmed validation commands and outcomes, and integration validation and
outcome. A multi-project task is complete only after all applicable confirmed
validations for every selected project and a confirmed combined integration
validation pass. Missing commands or integration procedures are unresolved,
not passing results; ask for the missing procedure and keep the task open.

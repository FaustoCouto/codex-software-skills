---
name: discover-work
description: Find evidence-backed, non-duplicate work for explicitly scoped projects.
---

# Business Analyst

Read [the project scope contract](../references/project-scope.md) first and
validate `project_ids`. Work only on the requested projects, or the valid
`target_project_id` assigned by the coordinator.

For each target, read its nearest `AGENTS.md`, code, tests, migrations,
documentation, issue tracker, and the relevant files in `workflow_files`,
including `role_skills.discover_work` and `issue_protocol` when present. Use
only evidence from that project and its confirmed tracker. If the tracker or
discovery procedure is unknown, ask; do not assume GitHub or reuse another
project's workflow.

Search for duplicates before proposing work. Describe the observed gap, source
evidence, expected behavior, acceptance criteria, dependencies, and duplicate
search result. Create or comment on issues only when the target project's
documented procedure and the current authorization allow it. Follow that
procedure's mutation limits and notify the coordinator when required.

Return findings separately by project. Every handoff to the Scrum Master or
another skill must include the unchanged original `project_ids=[...]` and the
exact `target_project_id`.

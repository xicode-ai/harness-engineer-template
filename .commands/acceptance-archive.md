---
name: "Harness: Acceptance Archive"
description: Verify final evidence after the user review checkpoint, archive the OpenSpec change, and produce an acceptance report.
category: Harness
tags: [harness, acceptance, archive, workflow]
---

# Command: acceptance-archive

## Purpose

Validate final evidence and archive the completed OpenSpec change.

## Inputs

- `.openspec/changes/<change-id>/`
- User confirmation that manual review is complete.
- Test evidence.
- Review reports.

## Responsible Agent

No autonomous agent. This command may run only after the user explicitly confirms their own manual review is complete.

## Required Skills

- `acceptance-archival`
- `openspec-validation`

## Project Coding Rules

No new code is reviewed in this command. Use prior `spec-review` and `code-review` outputs to confirm project coding rules were already considered.

## Procedure

1. Verify required artifacts exist.
2. Verify OpenSpec validation result.
3. Confirm review findings are fixed or accepted.
4. Confirm the user has explicitly completed manual review.
5. Archive the OpenSpec change.
6. Create the acceptance report.

## Output Artifacts

- `.openspec/archive/<date>-<change-id>/`
- `docs/acceptance/<change-id>-acceptance-report.md`

## Quality Gate

Acceptance report must link PRD, analysis, OpenSpec, implementation notes, review reports, test evidence, and the user's explicit review confirmation.

## Failure Handling

If evidence is missing, stop archival and leave the change open.

## Next Command

None. The change is complete.

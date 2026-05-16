---
name: "Harness: Acceptance Archive"
description: Verify final evidence, enforce approval gates, archive the OpenSpec change, and produce an acceptance report.
category: Harness
tags: [harness, acceptance, archive, workflow]
---

# Command: acceptance-archive

## Purpose

Validate final evidence and archive the completed OpenSpec change.

## Inputs

- `.openspec/changes/<change-id>/`
- `docs/acceptance/<change-id>-human-review.md`
- Test evidence.
- Review reports.

## Responsible Agent

Acceptance Officer.

## Required Skills

- `acceptance-archival`
- `openspec-validation`

## Enforced Rules

- `acceptance-rules`
- `artifact-traceability`
- `openspec-rules`

## Procedure

1. Verify required artifacts exist.
2. Verify OpenSpec validation result.
3. Confirm review findings are fixed or accepted.
4. Confirm human approval.
5. Archive the OpenSpec change.
6. Create the acceptance report.

## Output Artifacts

- `.openspec/archive/<date>-<change-id>/`
- `docs/acceptance/<change-id>-acceptance-report.md`

## Quality Gate

Acceptance report must link PRD, analysis, OpenSpec, implementation notes, review reports, test evidence, and human decision.

## Failure Handling

If evidence is missing, stop archival and leave the change open.

## Next Command

None. The change is complete.

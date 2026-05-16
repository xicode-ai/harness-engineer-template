---
name: acceptance-archival
description: Verify final evidence, user review confirmation, review resolution, and archive an accepted OpenSpec change. Use only after the user explicitly says their own manual review is complete.
license: MIT
compatibility: Requires an OpenSpec-compatible repository layout; OpenSpec CLI optional but recommended.
metadata:
  author: harness-engineer-template
  version: "1.0"
  generatedBy: codex
---

# Skill: acceptance-archival

## Trigger

Use when a change is approved and ready to archive.

## Purpose

Confirm evidence completeness, archive the OpenSpec change, and produce final acceptance report.

## Inputs

- OpenSpec change.
- User confirmation that manual review is complete.
- Test evidence.
- Review reports.

## Procedure

1. Verify all required artifacts exist.
2. Confirm OpenSpec validation passed.
3. Confirm review blockers are fixed or accepted by the user.
4. Confirm the user explicitly completed manual review.
5. Archive the OpenSpec change.
6. Write acceptance report.

## Outputs

- `.openspec/archive/<date>-<change-id>/`
- `docs/acceptance/<change-id>-acceptance-report.md`

## Quality Checklist

- Acceptance report links every evidence artifact.
- User-accepted risks are explicit.
- Missing evidence blocks archival.

## Adapters

None.

## Examples

Use only after the user explicitly confirms their own manual review is complete.

# Skill: acceptance-archival

## Trigger

Use when a change is approved and ready to archive.

## Purpose

Confirm evidence completeness, archive the OpenSpec change, and produce final acceptance report.

## Inputs

- OpenSpec change.
- Human review decision.
- Test evidence.
- Review reports.

## Procedure

1. Verify all required artifacts exist.
2. Confirm OpenSpec validation passed.
3. Confirm review blockers are fixed or accepted.
4. Confirm human approval.
5. Archive the OpenSpec change.
6. Write acceptance report.

## Outputs

- `.openspec/archive/<date>-<change-id>/`
- `docs/acceptance/<change-id>-acceptance-report.md`

## Quality Checklist

- Acceptance report links every evidence artifact.
- Accepted risks are explicit.
- Missing evidence blocks archival.

## Adapters

None.

## Examples

Use only after `human-review` approves the change.

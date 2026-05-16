# Skill: openspec-validation

## Trigger

Use when an OpenSpec change must be validated.

## Purpose

Verify OpenSpec structure, requirement mapping, and readiness for implementation or acceptance.

## Inputs

- `.openspec/changes/<change-id>/`

## Procedure

1. Check proposal, design, tasks, and specs exist.
2. Run the configured OpenSpec validation command when available.
3. Check feature-to-requirement mapping.
4. Record validation result.
5. Report blocking issues.

## Outputs

- `docs/reviews/<change-id>-spec-validation.md`

## Quality Checklist

- Validation command and result are recorded.
- Missing artifacts are listed.
- Requirement mapping gaps are explicit.

## Adapters

None.

## Examples

Use before implementation and before archival.

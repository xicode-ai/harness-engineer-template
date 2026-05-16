# Command: spec-create

## Purpose

Convert the PRD and business analysis report into an OpenSpec change.

## Inputs

- PRD document.
- `docs/analysis/<change-id>-business-analysis.md`

## Responsible Agent

Architect.

## Required Skills

- `openspec-authoring`
- `openspec-validation`

## Enforced Rules

- `engineering-governance`
- `artifact-traceability`
- `openspec-rules`

## Procedure

1. Read the PRD and business analysis report.
2. Identify affected capabilities.
3. Create `.openspec/changes/<change-id>/proposal.md`.
4. Create `.openspec/changes/<change-id>/design.md`.
5. Create `.openspec/changes/<change-id>/tasks.md`.
6. Create or update capability spec deltas under `.openspec/changes/<change-id>/specs/`.
7. Run OpenSpec validation.
8. Record assumptions, risks, and validation result.

## Output Artifacts

- `.openspec/changes/<change-id>/proposal.md`
- `.openspec/changes/<change-id>/design.md`
- `.openspec/changes/<change-id>/tasks.md`
- `.openspec/changes/<change-id>/specs/<capability>/spec.md`

## Quality Gate

OpenSpec validation must pass, or an explicit exception must be recorded before implementation.

## Failure Handling

If validation fails, update the OpenSpec change and rerun validation. If feature points cannot map to requirements, return to `prd-analyze`.

## Next Command

`tdd-develop`

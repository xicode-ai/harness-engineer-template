---
name: "Harness: Spec Review"
description: Validate that an OpenSpec change is complete, internally consistent, and aligned with implemented behavior.
category: Harness
tags: [harness, openspec, review, workflow]
---

# Command: spec-review

## Purpose

Validate that the OpenSpec change is internally consistent and still matches the implemented behavior.

## Inputs

- `.openspec/changes/<change-id>/`
- `docs/implementation/<change-id>-implementation-notes.md`

## Responsible Agent

Architect or Spec Reviewer.

## Required Skills

- `openspec-validation`

## Enforced Rules

- `openspec-rules`
- `artifact-traceability`

## Procedure

1. Run OpenSpec validation.
2. Check that every feature point maps to a requirement.
3. Check that every implemented behavior maps back to the OpenSpec change.
4. Record validation commands and results.
5. Produce a spec validation report.

## Output Artifacts

- `docs/reviews/<change-id>-spec-validation.md`

## Quality Gate

Validation must pass or list concrete blocking issues.

## Failure Handling

If the spec is incomplete, return to `spec-create`. If implementation does not match the spec, route to `tdd-develop`.

## Next Command

`code-review`

---
name: "Harness: Code Review"
description: Review implementation changes against OpenSpec, tests, maintainability, security, observability, and operational risk.
category: Harness
tags: [harness, code-review, quality, workflow]
---

# Command: code-review

## Purpose

Review implementation changes against OpenSpec, tests, maintainability, security, and operational risk.

## Inputs

- Implementation diff.
- `.openspec/changes/<change-id>/`
- `docs/implementation/<change-id>-implementation-notes.md`
- `docs/reviews/<change-id>-spec-validation.md`

## Responsible Agent

Code Reviewer.

## Required Skills

- `code-review`

## Project Coding Rules

Review implementation against relevant project coding rules from `.rules/`, especially:

- `coding-style.md`
- `testing-standards.md`
- `api-and-data-contracts.md`
- `error-handling.md`
- `security-and-privacy.md`
- `observability.md`

## Procedure

1. Inspect the implementation diff.
2. Compare behavior against OpenSpec requirements.
3. Check tests against requirements and risk.
4. Review correctness, maintainability, security, observability, and migration risk.
5. Produce structured findings ordered by severity.

## Output Artifacts

- `docs/reviews/<change-id>-code-review.md`

## Quality Gate

High and critical findings must be fixed or explicitly accepted by the user before acceptance archival.

## Failure Handling

If issues are found, route back to `tdd-develop` after recording findings.

## Next Command

Stop and wait for the user to perform their own review. Continue to `acceptance-archive` only after the user explicitly confirms review is complete.

---
name: "Harness: TDD Develop"
description: Implement an OpenSpec change using test-driven development, focused verification, regression checks, and implementation notes.
category: Harness
tags: [harness, tdd, development, workflow]
---

# Command: tdd-develop

## Purpose

Implement an OpenSpec change using test-driven development.

## Inputs

- `.openspec/changes/<change-id>/`
- `docs/analysis/<change-id>-business-analysis.md`
- Existing repository source code.

## Responsible Agent

Fullstack Developer.

## Required Skills

- `tdd-development`

## Project Coding Rules

Apply relevant project coding rules from `.rules/`, especially:

- `coding-style.md`
- `testing-standards.md`
- `api-and-data-contracts.md`
- `error-handling.md`
- `security-and-privacy.md`
- `observability.md`

## Procedure

1. Inspect the repository and detect language, build tool, and test framework.
2. Select the matching TDD adapter.
3. For each OpenSpec task, write a failing test first.
4. Run the focused test and capture the failing result.
5. Implement the minimal production change.
6. Run the focused test and capture the passing result.
7. Refactor where needed.
8. Run relevant regression tests.
9. Write implementation notes.

## Output Artifacts

- Production code changes.
- Test code changes.
- `docs/implementation/<change-id>-implementation-notes.md`

## Quality Gate

All relevant tests must pass, and implementation notes must include exact commands and summarized results.

## Failure Handling

If no test framework exists, propose a minimal test strategy before implementation. If TDD cannot be applied directly, record an exception and use characterization or integration tests.

## Next Command

`spec-review`

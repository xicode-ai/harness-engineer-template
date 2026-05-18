---
name: tdd-development
description: Implement OpenSpec tasks with test-driven development. Use when coding should follow failing test, minimal implementation, passing test, refactor, and verification evidence across any language.
license: MIT
compatibility: Runtime-neutral; selects language adapters from adapters/.
metadata:
  author: harness-engineer-template
  version: "1.0"
  generatedBy: codex
---

# Skill: tdd-development

## Trigger

Use when implementing an OpenSpec change.

## Purpose

Drive implementation through failing tests, minimal code, passing tests, refactoring, and verification evidence.

## Inputs

- OpenSpec change.
- Business analysis report.
- Existing codebase.

## Procedure

1. Detect ecosystem and test framework.
2. Read relevant project coding rules from `.rules/`.
3. Select the matching adapter from `adapters/`.
4. For each requirement, write a focused failing test.
5. Run the test and capture failure.
6. Implement minimal production code.
7. Run the focused test and capture pass.
8. Refactor only when behavior remains covered.
9. Run relevant regression tests.
10. Write implementation notes.

## Outputs

- Code changes.
- Test changes.
- `docs/implementation/<change-id>-implementation-notes.md`

## Quality Checklist

- Tests precede implementation.
- Code follows relevant project coding rules from `.rules/`.
- Test commands and outcomes are recorded.
- Implementation scope matches OpenSpec tasks.
- Exceptions are explicit.

## Adapters

- `adapters/generic.md`
- `adapters/java.md`
- `adapters/node.md`
- `adapters/python.md`
- `adapters/go.md`
- `adapters/rust.md`

## Examples

Use this skill inside `tdd-develop`.

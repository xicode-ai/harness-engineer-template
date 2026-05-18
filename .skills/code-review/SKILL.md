---
name: code-review
description: Review implementation against OpenSpec, tests, maintainability, security, observability, and operational risk. Use after implementation or whenever a structured review issue list is needed.
license: MIT
compatibility: Runtime-neutral Markdown skill.
metadata:
  author: harness-engineer-template
  version: "1.0"
  generatedBy: codex
---

# Skill: code-review

## Trigger

Use when implementation must be reviewed against OpenSpec and engineering rules.

## Purpose

Produce a structured issue list focused on correctness, spec alignment, tests, maintainability, security, and operational risk.

## Inputs

- Implementation diff.
- OpenSpec change.
- Test evidence.

## Procedure

1. Review requirements and implementation diff.
2. Check behavior against OpenSpec.
3. Read relevant project coding rules from `.rules/`.
4. Check test coverage against risk.
5. Identify findings.
6. Order findings by severity.
7. Write review report.

## Outputs

- `docs/reviews/<change-id>-code-review.md`

## Quality Checklist

- Findings include severity, location, requirement, problem, impact, recommendation, and status.
- Findings account for relevant project coding rules from `.rules/`.
- High and critical findings are clearly blocking.
- No-issue reviews still state residual risk.

## Adapters

None.

## Examples

Use after `spec-review`.

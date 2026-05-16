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
3. Check test coverage against risk.
4. Identify findings.
5. Order findings by severity.
6. Write review report.

## Outputs

- `docs/reviews/<change-id>-code-review.md`

## Quality Checklist

- Findings include severity, location, requirement, problem, impact, recommendation, and status.
- High and critical findings are clearly blocking.
- No-issue reviews still state residual risk.

## Adapters

None.

## Examples

Use after `spec-review`.

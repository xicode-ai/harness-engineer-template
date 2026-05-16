# Command: human-review

## Purpose

Record a human approval, rejection, change request, or accepted-risk decision.

## Inputs

- `docs/analysis/<change-id>-business-analysis.md`
- `.openspec/changes/<change-id>/`
- `docs/implementation/<change-id>-implementation-notes.md`
- `docs/reviews/<change-id>-spec-validation.md`
- `docs/reviews/<change-id>-code-review.md`

## Responsible Agent

Human Owner.

## Required Skills

- None. This is a human gate.

## Enforced Rules

- `engineering-governance`
- `acceptance-rules`

## Procedure

1. Present all evidence to the human reviewer.
2. Record the decision.
3. Record accepted risks and required follow-ups.
4. Route back to the correct command when changes are requested.

## Output Artifacts

- `docs/acceptance/<change-id>-human-review.md`

## Quality Gate

The decision must be explicit: Approved, Changes Requested, Rejected, or Approved With Accepted Risks.

## Failure Handling

If no human decision exists, block `acceptance-archive`.

## Next Command

`acceptance-archive`

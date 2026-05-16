# Gate Model

## Business Analysis Gate

Required artifacts:

- `docs/analysis/<change-id>-business-analysis.md`

Pass criteria:

- 5W1H, actors, flow, state model where applicable, feature matrix, risks, and OpenSpec scope are present.

## Specification Gate

Required artifacts:

- `.openspec/changes/<change-id>/proposal.md`
- `.openspec/changes/<change-id>/design.md`
- `.openspec/changes/<change-id>/tasks.md`
- `.openspec/changes/<change-id>/specs/<capability>/spec.md`

Pass criteria:

- OpenSpec validation passes or an exception is recorded.

## Development Gate

Required artifacts:

- Code changes.
- Test changes.
- `docs/implementation/<change-id>-implementation-notes.md`

Pass criteria:

- Focused and relevant regression tests pass.
- TDD evidence is recorded.

## Review Gate

Required artifacts:

- `docs/reviews/<change-id>-spec-validation.md`
- `docs/reviews/<change-id>-code-review.md`

Pass criteria:

- OpenSpec validation passes.
- High and critical review findings are fixed or accepted.

## Acceptance Gate

Required artifacts:

- `docs/acceptance/<change-id>-human-review.md`
- `docs/acceptance/<change-id>-acceptance-report.md`
- `.openspec/archive/<date>-<change-id>/`

Pass criteria:

- Human approval exists.
- Required evidence is linked.
- OpenSpec change is archived.

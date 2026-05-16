# Rule: OpenSpec

## Intent

Use OpenSpec as the canonical specification and acceptance contract.

## Requirements

- Every change must include proposal, design, tasks, and capability spec deltas when behavior changes.
- Every business feature point must map to an OpenSpec requirement or be explicitly marked out of scope.
- OpenSpec validation must run before implementation and before acceptance archival.
- Failed validation blocks development unless an explicit exception is recorded.
- Accepted OpenSpec changes must be archived after final approval.

## Gate Impact

Invalid or missing OpenSpec artifacts block `tdd-develop` and `acceptance-archive`.

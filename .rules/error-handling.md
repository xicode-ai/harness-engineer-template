# Rule: Error Handling

## Purpose

Define project-level expectations for validation, failures, retries, and recovery behavior.

## Requirements

- Make failure modes explicit and observable.
- Use existing project exception, result, or error-code conventions.
- Validate inputs before mutating state.
- Avoid swallowing exceptions without diagnostics.
- Use retries only when operations are idempotent or explicitly safe.
- Keep user-facing errors actionable and avoid exposing sensitive internals.

## Review Focus

- Unhandled error paths in changed control flow.
- State mutation before validation completes.
- Retry logic that can duplicate side effects.
- Error messages that expose secrets or internal implementation details.


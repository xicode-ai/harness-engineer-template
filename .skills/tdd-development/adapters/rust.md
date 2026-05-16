# TDD Adapter: Rust

## Detection

- `Cargo.toml`

## Test Strategy

- Prefer unit tests near implementation and integration tests under `tests/`.
- Use `Result` assertions for error behavior.
- Keep feature-flag-specific behavior explicit.

## Commands

- Focused test: `cargo test <test_name>`
- Regression test: `cargo test`

## Review Risks

- Missing error variant coverage.
- Feature flag drift.
- Overly broad integration tests.

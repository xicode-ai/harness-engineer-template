# TDD Adapter: Go

## Detection

- `go.mod`

## Test Strategy

- Place tests in `*_test.go` files near the package under test.
- Prefer table-driven tests for multiple cases.
- Use package-level tests unless external behavior requires integration tests.

## Commands

- Focused test: `go test ./path/to/package -run TestName`
- Regression test: `go test ./...`

## Review Risks

- Tests coupled to execution order.
- Missing error-path coverage.
- Race-sensitive code without race testing.

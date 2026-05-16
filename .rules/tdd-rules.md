# Rule: Test-Driven Development

## Intent

Make implementation evidence-driven and regression-resistant.

## Requirements

- Write a failing test before production code for every implementable behavior.
- Capture the focused failing result, passing result, and relevant regression result.
- Prefer the repository's existing test framework and conventions.
- If no test framework exists, propose a minimal test strategy before coding.
- If TDD cannot be applied directly, record an exception and use characterization or integration tests.

## Gate Impact

Missing test evidence blocks review unless a human owner accepts the risk.

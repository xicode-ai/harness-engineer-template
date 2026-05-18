# Rule: Testing Standards

## Purpose

Define project-level expectations for tests and verification evidence.

## Requirements

- Prefer the repository's existing test framework and naming conventions.
- Cover changed behavior with focused tests.
- Include normal path, failure path, and important boundary cases where practical.
- Keep tests deterministic and independent of external services unless explicitly integration-level.
- Record exact verification commands and summarized results in implementation notes.
- Avoid snapshot or fixture churn that does not improve behavioral confidence.

## Review Focus

- Missing regression coverage for changed behavior.
- Tests that assert implementation details instead of behavior.
- Flaky tests caused by time, randomness, network, or shared state.
- Broad integration tests where focused tests would provide faster feedback.


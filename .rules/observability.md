# Rule: Observability

## Purpose

Define project-level expectations for logs, metrics, traces, audit events, and operational diagnostics.

## Requirements

- Add observability only where it helps diagnose important behavior or failures.
- Follow existing logging levels, message style, and correlation ID conventions.
- Include enough context to debug failures without exposing sensitive data.
- Preserve auditability for business-critical state transitions.
- Avoid noisy logs in high-frequency paths.

## Review Focus

- Missing diagnostics for newly introduced failure paths.
- Logs without identifiers needed for support or incident analysis.
- Sensitive values in telemetry.
- Metrics or audit events that are inconsistent with existing naming.


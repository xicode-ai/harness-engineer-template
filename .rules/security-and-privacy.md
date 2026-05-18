# Rule: Security And Privacy

## Purpose

Define project-level expectations for secure and privacy-aware code changes.

## Requirements

- Never hardcode secrets, tokens, credentials, or private keys.
- Preserve authentication and authorization boundaries.
- Treat external input as untrusted.
- Avoid logging sensitive personal data, secrets, or security tokens.
- Follow existing encryption, masking, signing, and permission conventions.
- Consider abuse cases for user-facing or externally reachable behavior.

## Review Focus

- Missing authorization checks.
- Unsafe deserialization or injection surfaces.
- Sensitive data in logs, errors, metrics, or traces.
- Secret handling and configuration drift.


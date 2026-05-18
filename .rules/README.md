# Project Coding Rules

This directory stores project-specific coding standards and engineering conventions.

These rules are intentionally about code, not workflow orchestration. Workflow gates, artifact contracts, and command sequencing live under `.workflows/` and `.commands/`.

Replace or extend these files for each target project.

## Rule Files

- `coding-style.md`: naming, formatting, structure, comments, and maintainability.
- `testing-standards.md`: unit, integration, regression, and test data conventions.
- `api-and-data-contracts.md`: API, DTO, schema, compatibility, and migration rules.
- `error-handling.md`: validation, exceptions, retries, fallback, and failure semantics.
- `security-and-privacy.md`: authentication, authorization, secrets, privacy, and unsafe patterns.
- `observability.md`: logging, metrics, tracing, audit events, and operational diagnostics.

## Usage

Agents should read relevant files in this directory before modifying code or reviewing implementation.

If a repository already has coding standards, mirror them here or replace these generic rules with project-specific versions.


# Rule: API And Data Contracts

## Purpose

Define project-level expectations for API, schema, DTO, event, and data compatibility changes.

## Requirements

- Preserve backward compatibility unless the OpenSpec change explicitly allows a breaking change.
- Keep request, response, event, and persistence models coherent across layers.
- Validate inputs at clear boundaries.
- Document migration and rollout requirements for schema or contract changes.
- Avoid leaking internal implementation details through public contracts.

## Review Focus

- Breaking API or schema changes without migration strategy.
- DTO/entity coupling that exposes persistence internals.
- Missing validation for external inputs.
- Inconsistent field naming, nullability, enum values, or date/time semantics.


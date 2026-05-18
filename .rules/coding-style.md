# Rule: Coding Style

## Purpose

Define project-level code style and maintainability conventions.

## Requirements

- Follow the repository's existing formatting, naming, layering, and module conventions.
- Prefer small, focused changes that match nearby code.
- Keep functions and classes cohesive; avoid mixing unrelated responsibilities.
- Use clear names that reflect domain behavior, not implementation accidents.
- Add comments only when they explain non-obvious decisions, invariants, or trade-offs.
- Avoid broad refactors unless they are required for the requested change.

## Review Focus

- Inconsistent style compared with nearby code.
- Overly large functions or files introduced by the change.
- Hidden coupling or unclear ownership boundaries.
- Comments that restate code instead of explaining intent.


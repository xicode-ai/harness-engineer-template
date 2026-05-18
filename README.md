# Harness Engineer Template

Universal, enterprise-grade harness engineering template for AI-assisted software development.

This repository defines a reusable workflow that can support any language or framework by separating development into commands, rules, skills, agents, workflows, OpenSpec artifacts, and auditable evidence.

## Core Flow

```text
PRD
  -> prd-analyze
  -> spec-create
  -> tdd-develop
  -> spec-review
  -> code-review
  -> user manual review
  -> acceptance-archive
```

## Layers

| Layer | Path | Purpose |
| --- | --- | --- |
| Commands | `.commands/` | Lifecycle orchestration |
| Rules | `.rules/` | Project-specific coding standards |
| Skills | `.skills/` | Reusable task capabilities |
| Agents | `.agents/` | Codex subagent TOML configs for role-specific work |
| Workflows | `.workflows/` | End-to-end process and gate model |
| OpenSpec | `.openspec/` | Specification, change, and archive state |
| Docs | `docs/` | Analysis, implementation, review, and acceptance evidence |

## Recommended Usage

1. Start with a PRD.
2. Run `prd-analyze` to produce business analysis.
3. Run `spec-create` to produce an OpenSpec change.
4. Run `tdd-develop` to implement through tests.
5. Run `spec-review` and `code-review`.
6. Stop and let the user perform their own manual review.
7. After explicit user confirmation, complete the lifecycle with `acceptance-archive`.

## Design Specification

See `docs/superpowers/specs/2026-05-16-universal-harness-engineering-design.md`.

## Sample PRD

See `docs/examples/sample-prd.md`.

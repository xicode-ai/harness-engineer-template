---
name: openspec-authoring
description: Create an OpenSpec change from business analysis. Use when requirements need proposal, design, tasks, capability spec deltas, and feature-to-requirement mapping before development.
license: MIT
compatibility: Requires an OpenSpec-compatible repository layout; OpenSpec CLI optional but recommended.
metadata:
  author: harness-engineer-template
  version: "1.0"
  generatedBy: codex
---

# Skill: openspec-authoring

## Trigger

Use when business analysis must be converted into an OpenSpec change.

## Purpose

Create proposal, design, tasks, and capability spec deltas.

## Inputs

- PRD.
- Business analysis report.

## Procedure

1. Choose a stable `change-id`.
2. Identify affected capabilities.
3. Create proposal.
4. Create design.
5. Create task list.
6. Create spec deltas.
7. Map feature points to requirements.
8. Prepare for OpenSpec validation.

## Outputs

- `.openspec/changes/<change-id>/proposal.md`
- `.openspec/changes/<change-id>/design.md`
- `.openspec/changes/<change-id>/tasks.md`
- `.openspec/changes/<change-id>/specs/<capability>/spec.md`

## Quality Checklist

- Every requirement is testable.
- Every feature point is mapped or marked out of scope.
- Tasks are concrete enough for TDD implementation.
- Risks and assumptions are recorded.

## Adapters

None.

## Examples

Use this skill inside `spec-create`.

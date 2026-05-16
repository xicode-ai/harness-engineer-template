---
name: business-analysis
description: Convert a PRD into a structured business analysis report. Use when the user provides product requirements, asks for 5W1H analysis, use cases, process flows, state diagrams, feature matrices, or wants an OpenSpec-ready analysis before implementation.
license: MIT
compatibility: Runtime-neutral Markdown skill.
metadata:
  author: harness-engineer-template
  version: "1.0"
  generatedBy: codex
---

# Skill: business-analysis

## Trigger

Use when a PRD must be converted into a structured business analysis report.

## Purpose

Extract business intent, actors, flows, states, feature points, risks, and OpenSpec-ready scope.

## Inputs

- PRD.
- Optional domain context.

## Procedure

1. Identify business objective and success criteria.
2. Produce 5W1H analysis.
3. Identify actors and boundaries.
4. Produce Mermaid use case diagram.
5. Produce Mermaid process flow.
6. Produce Mermaid state diagram when domain state exists.
7. Build feature point matrix.
8. Record assumptions, risks, and open questions.
9. Write `docs/analysis/<change-id>-business-analysis.md`.

## Outputs

- Business analysis report.

## Quality Checklist

- The analysis maps business goals to feature points.
- Diagrams are readable as plain Mermaid.
- Risks and assumptions are explicit.
- Recommended OpenSpec scope is clear.

## Adapters

None.

## Examples

Use this skill before `spec-create`.

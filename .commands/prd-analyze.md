---
name: "Harness: PRD Analyze"
description: Analyze a PRD into 5W1H, use cases, process flow, state model, feature matrix, risks, and an OpenSpec-ready business analysis report.
category: Harness
tags: [harness, analysis, prd, workflow]
---

# Command: prd-analyze

## Purpose

Convert a PRD into a structured business analysis report that can be used as input for OpenSpec specification.

## Inputs

- PRD document path or pasted PRD content.
- Optional business context, user stories, issue links, customer feedback, or domain notes.

## Responsible Agent

Business Analyst.

## Required Skills

- `business-analysis`

## Enforced Rules

- `engineering-governance`
- `artifact-traceability`

## Procedure

1. Assign or confirm a stable `change-id`.
2. Read the PRD and supporting context.
3. Extract the business goal and scope.
4. Perform 5W1H analysis.
5. Identify actors and system boundaries.
6. Produce use case, process flow, and state model where applicable.
7. Extract the feature point matrix.
8. Record assumptions, ambiguities, risks, and open questions.
9. Write the business analysis report.

## Output Artifacts

- `docs/analysis/<change-id>-business-analysis.md`

## Quality Gate

The report must include executive summary, 5W1H, actors, use case diagram, process flow, feature matrix, non-functional requirements, risks, and recommended OpenSpec scope.

## Failure Handling

If the PRD is ambiguous, record questions and block `spec-create` unless the user approves explicit assumptions.

## Next Command

`spec-create`

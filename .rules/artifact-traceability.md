# Rule: Artifact Traceability

## Intent

Make every requirement, decision, implementation, test, review, and acceptance result traceable.

## Requirements

- Use a stable `change-id` for every lifecycle artifact.
- Link PRD, business analysis, OpenSpec change, implementation notes, reviews, user review confirmation, and acceptance report.
- Store generated artifacts under the paths defined by `.workflows/artifact-contracts.md`.
- Include exact validation and test commands in implementation or review notes.
- Do not archive a change when required artifacts are missing.

## Gate Impact

Missing traceability blocks acceptance archival.

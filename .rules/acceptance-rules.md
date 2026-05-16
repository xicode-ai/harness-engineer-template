# Rule: Acceptance

## Intent

Accept only changes with complete evidence and explicit user confirmation that manual review is complete.

## Requirements

- The user must explicitly confirm their own manual review is complete before archival.
- User-accepted risks must be listed explicitly.
- Acceptance reports must link all required evidence.
- Archived changes are immutable except for administrative correction notes.
- If archival fails, the OpenSpec change remains open.

## Gate Impact

Missing user confirmation, unresolved review blockers, or incomplete evidence blocks acceptance archival.

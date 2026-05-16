# Rule: Engineering Governance

## Intent

Ensure every AI-assisted change follows an auditable senior-engineer workflow.

## Requirements

- Do not start implementation from a PRD until business analysis and OpenSpec artifacts exist.
- Record assumptions before acting on ambiguous requirements.
- Keep changes scoped to the approved OpenSpec change.
- Preserve user manual review as a required checkpoint before acceptance archival.
- Record every exception with owner, reason, impact, and follow-up.

## Gate Impact

Violations block the next lifecycle command unless the user explicitly approves an exception.

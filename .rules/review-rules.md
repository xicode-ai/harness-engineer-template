# Rule: Review

## Intent

Ensure every change is reviewed for correctness, specification alignment, and operational risk.

## Requirements

- Review findings must be ordered by severity.
- Each finding must include severity, location, requirement, problem, impact, recommendation, and status.
- High and critical findings must be fixed or explicitly accepted by the user before acceptance archival.
- If no issues are found, the review must still state residual risks and test gaps.
- Review must not silently mutate scope or implementation without recording the finding.

## Gate Impact

Open high or critical findings block acceptance archival.

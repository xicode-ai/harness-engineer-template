# Artifact Contracts

## Change ID

Use this format:

```text
<domain>-<short-feature-name>-<yyyymmdd>
```

Example:

```text
membership-coupon-refund-20260516
```

## Required Artifact Paths

| Artifact | Path |
| --- | --- |
| Business analysis | `docs/analysis/<change-id>-business-analysis.md` |
| OpenSpec change | `.openspec/changes/<change-id>/` |
| Implementation notes | `docs/implementation/<change-id>-implementation-notes.md` |
| Spec validation | `docs/reviews/<change-id>-spec-validation.md` |
| Code review | `docs/reviews/<change-id>-code-review.md` |
| Acceptance report | `docs/acceptance/<change-id>-acceptance-report.md` |
| Archive | `.openspec/archive/<date>-<change-id>/` |

## Review Finding Format

```markdown
## Finding <number>: <title>

- Severity: Critical | High | Medium | Low | Nit
- Location: `<file>:<line>`
- Requirement: `<OpenSpec requirement id>`
- Problem:
- Impact:
- Recommendation:
- Status: Open | Fixed | Accepted Risk
```

## User Manual Review Checkpoint

The user performs manual review outside the automated command flow after `code-review` and before `acceptance-archive`.

The harness must stop at this checkpoint and wait for an explicit user instruction such as:

- Continue to acceptance archive.
- I reviewed it; archive it.
- Changes requested; return to implementation.
- I accept the listed risks; archive it.

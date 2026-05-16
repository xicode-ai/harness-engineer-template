# Universal Harness Engineering Implementation Plan

This implementation plan has been executed and superseded by the current repository templates and documentation.

Authoritative current references:

- `docs/superpowers/specs/2026-05-16-universal-harness-engineering-design.md`
- `docs/harness-engineering-manual.zh-CN.md`
- `.commands/`
- `.rules/`
- `.skills/`
- `.agents/`
- `.workflows/`

## Correction

The original draft treated manual user review as an executable command. The current harness design corrects that interpretation:

- User review is an external checkpoint performed by the user.
- The harness stops after `code-review` and waits for explicit user confirmation.
- Acceptance archival runs only after the user confirms their own review is complete.
- No agent or command approves work on the user's behalf.

## Agent Format Correction

The original draft used Markdown role contracts under `.agents/`. The current harness uses Codex subagent TOML files instead:

- `.agents/business-analyst.toml`
- `.agents/architect.toml`
- `.agents/fullstack-developer.toml`
- `.agents/code-reviewer.toml`

Each file follows the Codex subagent fields `name`, `description`, `model`, `model_reasoning_effort`, `sandbox_mode`, and `developer_instructions`.

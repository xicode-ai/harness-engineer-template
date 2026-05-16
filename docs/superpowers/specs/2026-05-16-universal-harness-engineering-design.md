# Universal Harness Engineering Design

## 1. Purpose

This document defines a universal, enterprise-grade harness engineering workflow that can support any programming language, framework, repository shape, or delivery platform.

The harness is not designed for one specific project. It is a reusable engineering control layer that standardizes how AI-assisted development moves from product requirements to business analysis, OpenSpec specification, test-driven implementation, review, user manual review checkpoint, and final acceptance archival.

The core design principle is separation of concerns:

- **Commands** orchestrate the development lifecycle.
- **Rules** define non-negotiable engineering constraints.
- **Skills** provide reusable task capabilities.
- **Agents** represent senior engineering roles with clear responsibilities.
- **Artifacts** preserve traceability between requirements, specifications, code, reviews, and acceptance decisions.

## 2. Design Goals

The harness must:

- Work for any language, including Java, Go, Python, JavaScript, TypeScript, Rust, C#, C++, and polyglot repositories.
- Support enterprise governance through explicit gates, traceable artifacts, and auditable decisions.
- Guide AI agents to think and work like senior engineers instead of directly jumping into code.
- Separate business analysis, architecture specification, implementation, review, and acceptance.
- Use OpenSpec as the canonical specification and acceptance contract.
- Use TDD as the default development discipline for feature and bugfix implementation.
- Allow user manual review at a formal checkpoint before acceptance archival.
- Be copyable into new repositories as a harness template.

The harness should initially be implemented as a specification template repository plus lightweight command conventions. It should leave room for future CLI, CI/CD, policy engine, and dashboard integration.

## 3. Non-Goals

This design does not prescribe:

- A specific programming language.
- A specific application framework.
- A specific AI provider or model.
- A specific CI/CD platform.
- A specific issue tracker or document management system.

It also does not replace user review. Instead, it creates stronger inputs for the user's manual review and makes acceptance decisions easier to audit.

## 4. Repository Structure

The generic harness repository should use this structure:

```text
.
├── .commands/
│   ├── prd-analyze.md
│   ├── spec-create.md
│   ├── tdd-develop.md
│   ├── spec-review.md
│   ├── code-review.md
│   └── acceptance-archive.md
├── .rules/
│   ├── engineering-governance.md
│   ├── artifact-traceability.md
│   ├── openspec-rules.md
│   ├── tdd-rules.md
│   ├── review-rules.md
│   └── acceptance-rules.md
├── .skills/
│   ├── business-analysis/
│   ├── openspec-authoring/
│   ├── tdd-development/
│   ├── openspec-validation/
│   ├── code-review/
│   └── acceptance-archival/
├── .agents/
│   ├── business-analyst.md
│   ├── architect.md
│   ├── fullstack-developer.md
│   └── code-reviewer.md
├── .workflows/
│   ├── universal-development-flow.md
│   ├── gate-model.md
│   └── artifact-contracts.md
├── .openspec/
│   ├── project.md
│   ├── specs/
│   ├── changes/
│   └── archive/
├── docs/
│   ├── analysis/
│   ├── implementation/
│   ├── reviews/
│   ├── acceptance/
│   └── superpowers/
└── README.md
```

Each folder has a distinct purpose:

- `.commands/` contains user-facing workflow commands.
- `.rules/` contains global constraints every command and agent must obey.
- `.skills/` contains reusable capabilities that can be invoked by agents.
- `.agents/` defines role prompts, responsibilities, inputs, outputs, and handoff rules.
- `.workflows/` defines end-to-end process choreography.
- `.openspec/` stores formal OpenSpec project context, changes, specs, and archives.
- `docs/` stores generated business analysis, implementation, review, and acceptance reports.

## 5. Layered Architecture

### 5.1 Command Layer

The command layer defines the lifecycle entry points. A command is a deterministic process contract, not just a prompt.

Every command should define:

- Purpose.
- Required inputs.
- Responsible agent.
- Required skills.
- Rules that must be enforced.
- Output artifacts.
- Quality gates.
- Next command.

Recommended commands:

| Command | Purpose | Primary Agent | Main Output |
| --- | --- | --- | --- |
| `prd-analyze` | Analyze PRD and extract business intent | Business Analyst | Business analysis report |
| `spec-create` | Convert analysis into OpenSpec change/spec | Architect | OpenSpec proposal, tasks, design |
| `tdd-develop` | Implement specification with TDD | Fullstack Developer | Code, tests, implementation notes |
| `spec-review` | Validate OpenSpec consistency and completeness | Architect or Spec Reviewer | Spec validation report |
| `code-review` | Review code against spec and engineering rules | Code Reviewer | Review issue list |
| `acceptance-archive` | Validate final acceptance and archive change after user manual review | No autonomous agent | Acceptance report and archived OpenSpec change |

### 5.2 Rules Layer

The rules layer defines enterprise constraints. Rules are global and should be enforced across all commands.

Core rules:

- A PRD-driven feature must not enter implementation until business analysis and OpenSpec artifacts exist.
- Every OpenSpec change must include proposal, design, task list, affected capabilities, and validation result.
- Implementation must follow TDD unless an explicit exception is recorded.
- Every test command and validation command must be captured in implementation notes.
- Code review must output a structured issue list, including severity, file reference, finding, impact, and recommendation.
- User manual review is an external checkpoint, not a command or agent-owned task.
- Acceptance archival must link PRD, analysis report, OpenSpec change, implementation notes, review report, test evidence, and the user's explicit review confirmation.

### 5.3 Skills Layer

Skills are reusable capabilities. They are not full workflows; they are focused tools used by agents inside commands.

Recommended skills:

| Skill | Responsibility |
| --- | --- |
| `business-analysis` | Convert PRD into 5W1H, use cases, flows, states, feature matrix, and analysis report |
| `openspec-authoring` | Create OpenSpec proposal, design, task list, and capability deltas |
| `tdd-development` | Drive failing test, minimal implementation, refactor, verification, and commit-ready notes |
| `openspec-validation` | Run or simulate OpenSpec validation and identify specification gaps |
| `code-review` | Review implementation for correctness, maintainability, security, testing, and spec alignment |
| `acceptance-archival` | Verify acceptance evidence and archive completed OpenSpec changes |

Skills should be language-neutral whenever possible. Language-specific details belong in adapters, for example:

```text
.skills/tdd-development/adapters/
├── java.md
├── node.md
├── python.md
├── go.md
├── rust.md
└── generic.md
```

### 5.4 Agent Layer

Agents model senior engineering roles. Each agent has clear authority and handoff requirements.

| Agent | Responsibility | Cannot Do |
| --- | --- | --- |
| Business Analyst | Interpret PRD and produce business analysis artifacts | Write production code |
| Architect | Convert analysis into OpenSpec and technical specification | Bypass OpenSpec validation |
| Fullstack Developer | Implement via TDD and produce verification evidence | Accept work without review |
| Code Reviewer | Review code and produce actionable issue list | Silently fix issues without recording findings |

Agent handoffs must always include:

- Input artifact references.
- Summary of decisions.
- Known assumptions.
- Open risks.
- Output artifact paths.
- Next expected command.

## 6. Universal Development Workflow

The end-to-end workflow is:

```text
PRD
  -> prd-analyze
  -> business analysis report
  -> spec-create
  -> OpenSpec proposal/design/tasks/spec deltas
  -> tdd-develop
  -> code and tests
  -> spec-review
  -> OpenSpec validation report
  -> code-review
  -> review issue list
  -> user manual review checkpoint
  -> user confirms review is complete or requests changes
  -> acceptance-archive
  -> archived OpenSpec change and acceptance report
```

The process has five gates:

| Gate | Required Before Passing |
| --- | --- |
| Business Analysis Gate | 5W1H, use cases, flow, state model, feature matrix, analysis report |
| Specification Gate | OpenSpec change exists and validates |
| Development Gate | TDD evidence, passing tests, implementation notes |
| Review Gate | Spec validation and code review issue list completed |
| Acceptance Gate | User review confirmation and archived OpenSpec change |

## 7. Business Analysis Flow

Input:

- PRD document.
- Optional business context.
- Optional user stories, issue links, customer feedback, or domain notes.

Process:

1. Extract the business goal.
2. Run 5W1H analysis.
3. Identify actors and boundaries.
4. Create use case model.
5. Create business process flow.
6. Create state transition model where domain state exists.
7. Extract feature points.
8. Build feature point matrix.
9. Identify assumptions, ambiguities, risks, and missing requirements.
10. Generate business analysis report.

Output:

```text
docs/analysis/<change-id>-business-analysis.md
```

The report should include:

- Executive summary.
- 5W1H table.
- Actor list.
- Use case diagram in Mermaid.
- Flowchart in Mermaid.
- State diagram in Mermaid when applicable.
- Feature point matrix.
- Non-functional requirements.
- Risks and open questions.
- Recommended OpenSpec change scope.

## 8. Specification Creation Flow

Input:

- PRD.
- Business analysis report.

Process:

1. Architect agent reads the PRD and business analysis report.
2. Architect identifies affected capabilities.
3. Architect creates OpenSpec change proposal.
4. Architect creates technical design.
5. Architect creates task list.
6. Architect updates or creates spec deltas.
7. Architect runs OpenSpec validation.
8. Architect records assumptions and unresolved questions.

Output:

```text
.openspec/changes/<change-id>/proposal.md
.openspec/changes/<change-id>/design.md
.openspec/changes/<change-id>/tasks.md
.openspec/changes/<change-id>/specs/<capability>/spec.md
```

Rules:

- No implementation should start before OpenSpec validation passes or an explicit exception is approved.
- OpenSpec tasks must be concrete enough for TDD development.
- Every feature point from the business matrix must map to one or more OpenSpec requirements or be explicitly marked out of scope.

## 9. TDD Development Flow

Input:

- OpenSpec change.
- Business analysis report.
- Existing codebase context.

Process:

1. Fullstack Developer agent inspects the repository.
2. Agent identifies language and test framework.
3. Agent selects the appropriate TDD adapter.
4. For each OpenSpec task:
   - Write failing test.
   - Run test and capture failure.
   - Implement minimal code.
   - Run test and capture pass.
   - Refactor if needed.
   - Run relevant regression tests.
   - Record verification evidence.
5. Agent updates implementation notes.

Output:

```text
docs/implementation/<change-id>-implementation-notes.md
```

Rules:

- TDD is the default.
- If the repository lacks a test framework, the developer must propose a minimal test strategy before coding.
- Changes should be scoped to the OpenSpec tasks.
- Test evidence must include exact commands and summarized results.

## 10. Specification And Code Review Flow

Input:

- OpenSpec change.
- Implementation diff.
- Test evidence.
- Business analysis report.

Process:

1. Run OpenSpec validation.
2. Check that implementation satisfies every OpenSpec requirement.
3. Check test coverage against requirements.
4. Run code review agent.
5. Produce structured findings.

Output:

```text
docs/reviews/<change-id>-spec-validation.md
docs/reviews/<change-id>-code-review.md
```

Code review issue format:

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

Rules:

- Findings must be ordered by severity.
- Review must focus on correctness, spec alignment, test gaps, maintainability, security, observability, and migration risk.
- If no issues are found, the review must explicitly state residual risks and test gaps.

## 11. User Manual Review Checkpoint

Input:

- Business analysis report.
- OpenSpec change.
- Implementation notes.
- Spec validation report.
- Code review report.

Process:

1. The harness stops after `code-review` and presents generated artifacts to the user.
2. The user performs their own manual review outside the command flow.
3. The user explicitly tells the assistant whether to continue to acceptance archival, return to implementation, or accept listed risks.

Rules:

- This checkpoint is not implemented as an executable command.
- No agent should approve work on the user's behalf.
- Acceptance archival cannot run until the user explicitly confirms their own review is complete.
- User-accepted risks must be explicit in the acceptance report.
- Requested changes must route back to the appropriate command, usually `spec-create`, `tdd-develop`, or `code-review`.

## 12. Acceptance Archival Flow

Input:

- OpenSpec change.
- User confirmation that manual review is complete.
- Test evidence.
- Review reports.

Process:

1. Verify that all required artifacts exist.
2. Check OpenSpec validation result.
3. Confirm code review findings are resolved or explicitly accepted by the user.
4. Confirm the user has completed manual review.
5. Archive OpenSpec change.
6. Create acceptance report.

Output:

```text
.openspec/archive/<date>-<change-id>/
docs/acceptance/<change-id>-acceptance-report.md
```

Rules:

- The acceptance report must contain links to all evidence.
- Archived changes must remain immutable except for administrative correction notes.
- If archival fails, the change remains open.

## 13. Artifact Traceability Model

Every change should be traceable through a stable `change-id`.

Recommended ID format:

```text
<domain>-<short-feature-name>-<yyyymmdd>
```

Example:

```text
membership-coupon-refund-20260516
```

Traceability chain:

```text
PRD
  -> docs/analysis/<change-id>-business-analysis.md
  -> .openspec/changes/<change-id>/
  -> implementation diff
  -> docs/implementation/<change-id>-implementation-notes.md
  -> docs/reviews/<change-id>-spec-validation.md
  -> docs/reviews/<change-id>-code-review.md
  -> user manual review checkpoint
  -> docs/acceptance/<change-id>-acceptance-report.md
  -> .openspec/archive/<date>-<change-id>/
```

## 14. Command Contract Template

Every command file in `.commands/` should follow this structure:

```markdown
---
name: "Harness: <Display Name>"
description: <One sentence describing when this command should be used and what it produces.>
category: Harness
tags: [harness, workflow]
---

# Command: <command-name>

## Purpose

## Inputs

## Responsible Agent

## Required Skills

## Enforced Rules

## Procedure

## Output Artifacts

## Quality Gate

## Failure Handling

## Next Command
```

This mirrors the Claude command format used under `.claude/commands/`, while keeping the command body portable across AI tools and execution environments.

## 15. Agent Contract Template

Every agent file in `.agents/` should follow this structure:

```markdown
# Agent: <agent-name>

## Mission

## Responsibilities

## Inputs

## Outputs

## Required Skills

## Rules

## Handoff Protocol

## Refusal Conditions
```

Refusal conditions are important in enterprise workflows. For example, the Fullstack Developer should refuse to implement when OpenSpec does not exist, unless the user explicitly approves an exception.

## 16. Skill Contract Template

Every skill directory in `.skills/` should include a `SKILL.md` with this structure:

```markdown
---
name: <skill-name>
description: <Trigger-focused description. Include when to use the skill and what it does.>
license: MIT
compatibility: <Runtime, CLI, or repository requirements.>
metadata:
  author: harness-engineer-template
  version: "1.0"
  generatedBy: codex
---

# Skill: <skill-name>

## Trigger

## Purpose

## Inputs

## Procedure

## Outputs

## Quality Checklist

## Adapters

## Examples
```

This mirrors the Claude Skill format used under `.claude/skills/`. Language-specific or platform-specific behavior should live under adapters rather than in the core skill.

## 17. Language Adapter Strategy

The harness should detect or accept the target language and select the matching adapter.

Recommended adapter responsibilities:

- Detect build tool.
- Detect test framework.
- Identify standard source and test directories.
- Provide test command examples.
- Define common review risks.
- Define common project-specific artifact conventions.

Example adapter mapping:

| Ecosystem | Detection Signals | Test Command Examples |
| --- | --- | --- |
| Java Maven | `pom.xml` | `mvn test`, `mvn -pl <module> test` |
| Java Gradle | `build.gradle`, `settings.gradle` | `./gradlew test` |
| Node | `package.json` | `npm test`, `pnpm test`, `yarn test` |
| Python | `pyproject.toml`, `requirements.txt` | `pytest`, `python -m pytest` |
| Go | `go.mod` | `go test ./...` |
| Rust | `Cargo.toml` | `cargo test` |
| .NET | `*.csproj`, `*.sln` | `dotnet test` |

## 18. Governance And Audit

The enterprise harness should support auditability through:

- Stable change IDs.
- Required artifact paths.
- Explicit gate pass/fail states.
- User review confirmation records.
- Accepted risk records.
- Test evidence.
- Review issue status.
- Immutable acceptance archives.

Future automation can turn these artifacts into:

- CI checks.
- Pull request templates.
- Release readiness reports.
- Compliance dashboards.
- Engineering metrics.

## 19. Error Handling

Common failure modes:

| Failure | Required Handling |
| --- | --- |
| PRD is ambiguous | Business Analyst records questions and blocks spec creation unless owner approves assumptions |
| OpenSpec validation fails | Architect fixes spec or records exception |
| No test framework exists | Developer proposes minimal test strategy before implementation |
| TDD cannot be applied directly | Developer records exception and uses characterization or integration tests |
| Code review finds high severity issue | Work returns to development before acceptance archival unless the user explicitly accepts the risk |
| User requests changes during manual review | Route back to the correct command |
| Acceptance evidence missing | Acceptance archival fails and change remains open |

## 20. Example End-To-End Scenario

Given a PRD for a new coupon refund capability:

1. Run `prd-analyze`.
2. Generate `docs/analysis/membership-coupon-refund-20260516-business-analysis.md`.
3. Run `spec-create`.
4. Generate `.openspec/changes/membership-coupon-refund-20260516/`.
5. Run `tdd-develop`.
6. Implement code and tests according to OpenSpec tasks.
7. Generate implementation notes.
8. Run `spec-review`.
9. Generate spec validation report.
10. Run `code-review`.
11. Generate review issue list.
12. Stop and let the user perform manual review.
13. After the user explicitly confirms review is complete, run `acceptance-archive`.
14. Archive OpenSpec change and generate final acceptance report.

## 21. Initial Implementation Recommendation

The first version of this harness should be implemented in three stages:

### Stage 1: Documentation Skeleton

Create `.commands/`, `.rules/`, `.skills/`, `.agents/`, `.workflows/`, `.openspec/`, and `docs/` templates.

### Stage 2: Example Workflow

Add one complete example change using a language-neutral sample PRD. This validates that the artifact chain is understandable.

### Stage 3: Lightweight Automation

Add optional scripts or CLI wrappers that validate artifact existence, OpenSpec structure, and gate completion.

The first version should avoid heavy platform assumptions. It should make the workflow executable by humans and agents before adding orchestration software.

## 22. Default Decisions And Extension Points

To keep the initial implementation portable and executable, the first version should use these defaults:

- Command files remain runtime-neutral Markdown first.
- The harness includes templates plus one bundled example workflow.
- User review confirmation is represented in the acceptance report first, with optional YAML front matter reserved for automation.
- The first automation layer uses language-neutral validation scripts only after the documentation skeleton and example workflow exist.

Future versions may add runtime-specific command adapters, machine-readable policy files, richer CI checks, and dashboards. Those extensions must preserve the same artifact contracts and gate model defined in this design.

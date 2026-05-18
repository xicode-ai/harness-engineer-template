# 通用 Harness 工程化开发流程说明书

## 1. 这套 Harness 是什么

这套 harness 是一个面向企业级软件研发的 AI 工程化流程模板。它不是为某一个具体业务系统设计的，也不绑定 Java、Go、Python、Node.js 或任何特定框架。

它的核心目标是把 AI 辅助开发从“直接写代码”升级为一套可审计、可追踪、可复用的工程流程：

```text
PRD
  -> 业务分析
  -> OpenSpec 规格
  -> TDD 开发
  -> 规格审查
  -> 代码审查
  -> 用户手动审核检查点
  -> 验收归档
```

这套流程模拟的是一名高级工程师或研发团队的工作方式：先理解业务，再形成规格，再编码，再审查，再验收，而不是拿到需求后马上修改代码。

## 2. 当前项目里的实际落点

当前项目中，harness 模板主要保存在这些目录：

```text
.commands/      命令编排层
.rules/         项目编码规范层
.skills/        能力技能层
.agents/        Codex 子代理配置层
.workflows/     流程与门禁层
.openspec/      OpenSpec 规格层
docs/           分析、实现、评审、验收等文档产物
```

需要特别注意：

- `.commands/` 和 `.skills/` 是通用模板目录。
- `.commands/*.md` 已经补齐类似 `.claude/commands/` 的 YAML frontmatter。
- `.skills/*/SKILL.md` 已经补齐类似 `.claude/skills/` 的 YAML frontmatter。
- 但它们目前还没有同步复制到 `.claude/commands/` 和 `.claude/skills/` 下。
- 因此，如果运行环境只识别 `.claude` 目录，需要再做一次适配或同步。

换句话说：当前这套 harness 已经具备规范结构，但还没有完全变成 Claude runtime 直接加载的命令和技能集合。

## 3. 分层设计

这套 harness 按照四个核心层次设计：Commands、Rules、Skills、Agents。

### 3.1 Commands：流程编排层

Commands 是研发流程的入口。每个 command 都是一段标准化流程，而不是一句提示词。

当前已有 6 个命令：

| 命令 | 作用 |
| --- | --- |
| `prd-analyze` | 将 PRD 转换为业务分析报告 |
| `spec-create` | 基于 PRD 和分析报告创建 OpenSpec 规格 |
| `tdd-develop` | 基于 OpenSpec 进行 TDD 开发 |
| `spec-review` | 验证 OpenSpec 与实现的一致性 |
| `code-review` | 审查代码、测试、风险和规格对齐情况 |
| `acceptance-archive` | 完成验收并归档 OpenSpec change |

每个 command 都包含：

- 用途
- 输入
- 负责 agent
- 需要的 skill
- 需要读取的项目编码规范
- 执行步骤
- 输出产物
- 质量门禁
- 失败处理
- 下一步 command

### 3.2 Rules：项目编码规范层

Rules 用来承载每个具体项目的代码相关规范，而不是流程治理规则。流程顺序、产物门禁、验收条件放在 `.commands/` 和 `.workflows/` 中，`.rules/` 只表达“这个项目的代码应该怎么写、怎么测、怎么审”。

当前已有 6 类项目编码规范模板：

| 规则 | 作用 |
| --- | --- |
| `coding-style.md` | 命名、格式、结构、注释和可维护性 |
| `testing-standards.md` | 单测、集成测试、回归测试和验证证据 |
| `api-and-data-contracts.md` | API、DTO、Schema、兼容性和迁移约定 |
| `error-handling.md` | 校验、异常、重试、降级和失败语义 |
| `security-and-privacy.md` | 鉴权、密钥、敏感数据、隐私和不安全输入 |
| `observability.md` | 日志、指标、链路追踪、审计事件和诊断信息 |

Rules 的价值是让 agent 在进入规格、开发和 review 时遵守当前项目的代码约定。例如：

- Java 项目可能要求特定包结构、异常类型和 MyBatis XML 风格。
- Node 项目可能要求特定 lint、测试命名和 API response 格式。
- Go 项目可能要求表驱动测试和错误包装约定。
- 金融或会员系统可能要求审计日志、幂等和敏感字段脱敏。

换句话说，`.rules/` 应该是每个项目可以替换的“编码规范包”。

### 3.3 Skills：能力技能层

Skills 是可复用能力。它们不是完整流程，而是 agents 在执行 commands 时调用的专项能力。

当前已有 6 个核心 skill：

| Skill | 作用 |
| --- | --- |
| `business-analysis` | PRD 分析、5W1H、用例、流程、状态、功能矩阵 |
| `openspec-authoring` | 编写 OpenSpec proposal、design、tasks、spec delta |
| `tdd-development` | 按 TDD 执行失败测试、最小实现、通过测试、重构 |
| `openspec-validation` | 验证 OpenSpec 结构和需求映射 |
| `code-review` | 输出结构化代码审查问题清单 |
| `acceptance-archival` | 检查证据完整性并归档验收 |

其中 `tdd-development` 下还有语言适配器：

```text
.skills/tdd-development/adapters/
├── generic.md
├── java.md
├── node.md
├── python.md
├── go.md
└── rust.md
```

这些 adapter 负责处理不同语言的测试命令、目录习惯和常见风险。例如：

- Java Maven 使用 `mvn -Dtest=<TestClass> test`
- Node 使用 `npm test`、`pnpm test` 或 `yarn test`
- Python 使用 `python -m pytest`
- Go 使用 `go test ./...`
- Rust 使用 `cargo test`

### 3.4 Agents：Codex 子代理配置层

Agents 模拟一个企业研发团队里的专业角色。当前项目使用 Codex subagent 的标准 TOML 格式，而不是 Markdown 角色说明。

当前已有 4 个 agent：

| 文件 | 职责 | 沙箱 |
| --- | --- | --- |
| `.agents/business-analyst.toml` | 分析 PRD，产出业务分析报告 | `workspace-write` |
| `.agents/architect.toml` | 基于业务分析创建 OpenSpec 规格 | `workspace-write` |
| `.agents/fullstack-developer.toml` | 基于规格执行 TDD 开发 | `workspace-write` |
| `.agents/code-reviewer.toml` | 审查实现和测试质量 | `read-only` |

每个 agent 都定义了：

- `name`
- `description`
- `model`
- `model_reasoning_effort`
- `sandbox_mode`
- `developer_instructions`

`developer_instructions` 中继续保留使命、输入、工作步骤、质量检查、返回格式和拒绝条件。拒绝条件很关键，它让 agent 不会越权。例如 Fullstack Developer 在没有 OpenSpec change 时应拒绝实现，Code Reviewer 只能输出审查问题清单，不能替用户批准进入验收。

## 4. 端到端流程

完整流程定义在：

```text
.workflows/universal-development-flow.md
```

流程如下：

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

这个流程最大的价值是把“需求到代码”的链路拆成多个可检查阶段。每个阶段都有明确输入、输出和门禁。

## 5. 五个质量门禁

门禁定义在：

```text
.workflows/gate-model.md
```

### 5.1 业务分析门禁

必须存在：

```text
docs/analysis/<change-id>-business-analysis.md
```

报告应包含：

- 业务目标
- 5W1H
- 参与者
- 用例图
- 流程图
- 状态图，适用于有状态流转的业务
- 功能点矩阵
- 风险和假设
- 推荐 OpenSpec 范围

### 5.2 规格门禁

必须存在：

```text
.openspec/changes/<change-id>/proposal.md
.openspec/changes/<change-id>/design.md
.openspec/changes/<change-id>/tasks.md
.openspec/changes/<change-id>/specs/<capability>/spec.md
```

并且 OpenSpec 验证应通过，或者记录明确例外。

### 5.3 开发门禁

必须存在：

```text
docs/implementation/<change-id>-implementation-notes.md
```

并且记录：

- 写了哪些测试
- 哪些测试先失败
- 如何实现最小代码
- 哪些测试通过
- 回归测试结果

### 5.4 审查门禁

必须存在：

```text
docs/reviews/<change-id>-spec-validation.md
docs/reviews/<change-id>-code-review.md
```

高优先级和严重问题必须修复，或者被用户明确接受为风险。

### 5.5 验收门禁

必须存在：

```text
docs/acceptance/<change-id>-acceptance-report.md
.openspec/archive/<date>-<change-id>/
```

用户没有明确确认自己已完成手动审核，不允许归档。

## 6. 产物追踪模型

产物契约定义在：

```text
.workflows/artifact-contracts.md
```

每个需求都应该有一个稳定的 `change-id`：

```text
<domain>-<short-feature-name>-<yyyymmdd>
```

示例：

```text
membership-coupon-refund-20260516
```

完整追踪链路：

```text
PRD
  -> docs/analysis/<change-id>-business-analysis.md
  -> .openspec/changes/<change-id>/
  -> docs/implementation/<change-id>-implementation-notes.md
  -> docs/reviews/<change-id>-spec-validation.md
  -> docs/reviews/<change-id>-code-review.md
  -> 用户手动审核检查点
  -> docs/acceptance/<change-id>-acceptance-report.md
  -> .openspec/archive/<date>-<change-id>/
```

这让后续审计可以回答几个关键问题：

- 这个代码变更来自哪个 PRD？
- PRD 中的功能点是否都映射到了规格？
- 规格是否都有测试覆盖？
- 测试是否真的执行过？
- 审查发现了哪些问题？
- 用户是否明确确认完成手动审核？
- 哪些风险被接受了？

## 7. 如何使用这套 Harness

### 7.1 准备 PRD

可以从示例开始：

```text
docs/examples/sample-prd.md
```

也可以把真实 PRD 放在项目文档目录中。

### 7.2 执行业务分析

使用 `prd-analyze`，产出：

```text
docs/analysis/<change-id>-business-analysis.md
```

这一阶段重点不是写技术方案，而是把业务讲清楚。

### 7.3 创建 OpenSpec

使用 `spec-create`，产出：

```text
.openspec/changes/<change-id>/
```

这一阶段由 Architect 负责，把业务功能点转成可实现、可测试、可验收的规格。

### 7.4 执行 TDD 开发

使用 `tdd-develop`。

Fullstack Developer 需要先识别项目语言和测试框架，然后选择适配器，例如 Java、Node、Python、Go 或 Rust。

开发过程应遵循：

```text
写失败测试
  -> 运行并确认失败
  -> 写最小实现
  -> 运行并确认通过
  -> 必要时重构
  -> 运行回归测试
  -> 记录实现说明
```

### 7.5 执行规格和代码审查

使用：

```text
spec-review
code-review
```

审查结果应形成结构化问题清单，而不是一句“看起来没问题”。

### 7.6 用户手动审核检查点

`code-review` 结束后，harness 应停止继续执行，让用户自己阅读分析报告、OpenSpec、实现说明、规格验证报告和代码审查清单。

这是一个外部检查点，不是 command，也不由 agent 代替完成。

用户可以明确给出下一步指令：

- 继续验收归档
- 我已审核，归档
- 有修改意见，回到开发
- 我接受这些风险，继续归档

### 7.7 验收归档

使用 `acceptance-archive`。

该命令只能在用户明确确认自己已完成手动审核后执行。它检查证据完整性，归档 OpenSpec change，并生成验收报告。

## 8. 当前版本的优点

### 8.1 语言无关

这套 harness 没有绑定具体语言。语言差异通过 adapter 解决，核心流程保持一致。

### 8.2 流程可审计

每一步都有产物路径和质量门禁，可以在代码审查、合规检查、上线前评审中复用。

### 8.3 Agent 职责清晰

不同 agent 有不同职责和拒绝条件，降低了 AI 越权执行的风险。

### 8.4 适合企业落地

它保留了用户手动审核和风险接受机制，适合企业研发流程，而不是完全自动化的个人脚本。

### 8.5 可以逐步自动化

当前是文档优先，后续可以增加 CLI、CI 检查、PR 模板和 dashboard，而不需要推翻流程设计。

## 9. 当前版本的不足

### 9.1 尚未完全接入 `.claude`

虽然 `.commands` 和 `.skills` 已经使用 Claude 风格 frontmatter，但它们还没有复制到：

```text
.claude/commands/
.claude/skills/
```

如果目标是让 Claude 直接识别 slash command 和 skill，需要增加同步层。

### 9.2 OpenSpec 仍是结构约定

当前 `.openspec/` 是通用结构。项目中同时存在未跟踪的 `openspec/` 目录，这可能说明实际 OpenSpec CLI 使用的是非隐藏目录。

后续需要统一：

- 使用 `.openspec/`
- 还是使用 `openspec/`
- 或者两者做兼容映射

### 9.3 缺少自动校验脚本

目前验证主要靠人工或 agent 执行命令。后续可以增加：

- 检查必需文件是否存在
- 检查 frontmatter 是否完整
- 检查 command 是否引用了存在的 skill/rule/agent
- 检查 `change-id` 产物链是否完整

### 9.4 缺少完整示例变更

现在有 sample PRD，但还没有一条完整示例：

```text
sample PRD
  -> analysis
  -> OpenSpec change
  -> implementation notes
  -> review reports
  -> user manual review checkpoint
  -> acceptance report
```

这个示例会非常有助于团队理解和复用。

## 10. 推荐下一步

### 10.1 同步为 Claude 可直接使用的版本

建议增加：

```text
.claude/commands/harness/
.claude/skills/harness-business-analysis/
.claude/skills/harness-openspec-authoring/
.claude/skills/harness-tdd-development/
.claude/skills/harness-openspec-validation/
.claude/skills/harness-code-review/
.claude/skills/harness-acceptance-archival/
```

这样可以让 Claude 运行时直接识别这些命令和技能。

### 10.2 统一 OpenSpec 目录策略

建议明确到底采用：

```text
.openspec/
```

还是：

```text
openspec/
```

如果要兼容 OpenSpec CLI，应优先参考 CLI 默认目录。

### 10.3 增加 harness 校验脚本

建议增加一个轻量校验命令，例如：

```text
scripts/verify-harness
```

检查：

- command frontmatter
- skill frontmatter
- 必需目录
- 必需 rules
- 必需 agents
- workflow 引用一致性
- docs 产物链完整性

### 10.4 增加完整样例流程

基于：

```text
docs/examples/sample-prd.md
```

补齐一套完整示例产物，帮助团队直接照着跑。

## 11. 总结

当前这套 harness 已经完成了企业级研发流程的基础骨架：

- 用 Commands 编排流程
- 用 Rules 约束工程质量
- 用 Skills 沉淀可复用能力
- 用 Agents 划分角色职责
- 用 Workflows 串联阶段和门禁
- 用 OpenSpec 承载规格和验收合同
- 用 Docs 保存全链路证据

它现在最适合作为“通用企业级 harness 模板仓库”的第一版。下一步的重点不是继续扩写概念，而是把它接入实际运行环境，并补一条完整示例流程，让团队能真正拿 PRD 跑通一次从分析到验收归档的闭环。

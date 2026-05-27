# 04 - 需求登记册

## 用途

需求登记册（Requirements Register）是项目需求的唯一可信来源，记录每个需求的完整信息、状态、优先级和验收标准。

## 格式模板

```markdown
# 需求登记册

| requirement_id | title | description | source | priority | type | status | acceptance_criteria | in_scope | out_of_scope_notes | dependencies | risks | owner | created_at | updated_at |
|---------------|-------|-------------|--------|----------|------|--------|-------------------|----------|-------------------|-------------|-------|-------|------------|------------|
| REQ-001 | [标题] | [描述] | [Human Owner/竞品分析/缺陷报告] | P0/P1/P2/P3 | [类型] | [状态] | [标准] | [是/否] | [如有] | [如有] | [如有] | [人] | [日期] | [日期] |
```

## 必需字段说明

| 字段 | 说明 |
|------|------|
| requirement_id | 唯一标识，格式 REQ-XXX，从 001 起编号 |
| title | 简短标题，≤50 字 |
| description | 完整描述，包含业务背景和具体要求 |
| source | 需求来源：Human Owner / 竞品分析 / 缺陷报告 / 法规要求 / 技术优化 |
| priority | P0（绝对必须）/ P1（高优先）/ P2（中优先）/ P3（低优先） |
| type | 需求类型（见下表） |
| status | 当前状态（见状态机） |
| acceptance_criteria | 验收标准，每条标准一行，必须可量化验证 |
| in_scope | 明确该需求是否在当前范围基线内 |
| out_of_scope_notes | 如果 in_scope=否，记录排除说明 |
| dependencies | 依赖的其他 REQ 或外部依赖 |
| risks | 与该需求相关的已知风险 |
| owner | 负责人，通常为 Human Owner 或 PM AI |
| created_at | 首次记录日期 |
| updated_at | 最后修改日期 |

## 需求类型

| 类型 | 说明 |
|------|------|
| business | 业务需求，解决业务目标或问题 |
| functional | 功能需求，系统应提供的具体功能 |
| non_functional | 非功能需求，性能、安全、可用性等 |
| data | 数据需求，数据结构、数据质量、数据迁移 |
| integration | 集成需求，与外部系统或服务的对接 |
| security | 安全需求，身份验证、授权、数据保护 |
| operational | 运维需求，部署、监控、备份、恢复 |
| reporting | 报表需求，指标定义、报告格式 |
| documentation | 文档需求，用户文档、API 文档、技术文档 |
| governance | 治理需求，合规、审计、政策 |

## 状态机

```
proposed → clarified → approved → in_progress → implemented → accepted
                                          ↘ rejected
                                          ↘ parked
                                          ↘ changed
```

| 状态 | 定义 |
|------|------|
| proposed | 已记录，待澄清 |
| clarified | 已澄清，验收标准已定义 |
| approved | Human Owner 确认纳入当前范围 |
| in_progress | 正在实现 |
| implemented | Coder 完成，等待验收 |
| accepted | Human Owner 确认满足验收标准 |
| rejected | Human Owner 确认不纳入（保留记录，说明拒绝原因） |
| parked | 暂时搁置（资源不足或等待外部条件） |
| changed | 范围或验收标准已变更，需重新评估 |

## 优先级判定

| 等级 | 定义 | 说明 |
|------|------|------|
| P0 | 绝对必须 | 没有它，系统无法运行，或核心价值无法展示，或安全/合规/数据完整性基线失败 |
| P1 | 高优先 | 系统能跑，但核心用户工作流严重受损，或 MVP 价值显著下降 |
| P2 | 中优先 | 体验、效率或完整性降低，但核心工作流仍可用 |
| P3 | 低优先 | 锦上添花，或未来版本考虑 |

**判定方法**：按顺序回答以下问题，确定优先级上限：

1. **安全/合规/数据完整性**：没有该需求，是否存在安全/合规/数据完整性违规？
   - 是 → **P0**（立即处理）
2. **核心价值**：没有该需求，核心价值还能演示吗？
   - 否 → **P0**
3. **主流程**：没有该需求，用户能完成主要工作流吗？
   - 否 → **P1**
4. **可否延后**：能安全地推迟到后续版本吗？
   - 能 → **P2/P3**
   - 不能 → **P1**

## 更新规则

1. 每当 Human Owner 提出新需求，48 小时内记录到登记册
2. 每次状态变化必须记录日期和变化原因
3. 需求描述必须完整，不允许"待补充"
4. 每个需求必须有关联依赖和风险（如有）
5. updated_at 字段每次修改必须同步更新

## Backlog 管理（敏捷模式）

在敏捷交付模式下，需求登记册的"proposed/clarified"列表即 Backlog。

Backlog 维护规则：
- **Refinement（细化）**：PM AI 定期与 Human Owner 一起细化 Backlog 中的需求，确保每条有验收标准
- **Grooming（清理）**：定期清理 rejected 或长期 parked 的需求
- **优先级重排**：每次 Sprint 规划前重排 Backlog
- **不可压缩规则**：当 Backlog 中 P0/P1 需求未完成时，不允许把 P2/P3 排在前面

## 需求变更

需求变更通过变更控制流程处理（references/09）。不允许：
- Human Owner 口头要求后直接执行
- Coder 自行决定增加或修改需求
- PM AI 自行扩大或缩小需求范围

变更后的 REQ 状态变更为"changed"，然后重新评估是否进入 approved。

## 常见陷阱

- **需求镀金（Gold Plating）**：Coder 在验收标准之外自行增加功能。PM AI 必须用验收标准做 Scope Creep Firewall。
- **范围蠕动**：多个小需求累积导致范围超出基线。每个需求单独记录，累积评估影响。
- **模糊需求**：描述无法指导实现或验收。必须追问到可量化标准。
- **缺少 out_of_scope_notes**：不清楚边界在哪里，容易引发范围争议。
- **缺少 dependencies 和 risks**：低估了需求之间的关联性和风险。

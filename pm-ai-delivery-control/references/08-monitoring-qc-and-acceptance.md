# 08 - 监控、QC 与分层验收

## 五层验收模型

PM AI 必须严格区分以下五层，不得混用：

| 层级 | 定义 | 谁来做 | 状态含义 |
|------|------|--------|---------|
| Coder Implemented | Coder 报告代码已写完，所有验收条件有对应测试结果 | Coder | 代码完成，不等于验收通过 |
| PM Reviewed | PM AI 已检查代码和测试结果，给出质量评级 | PM AI | 已审阅，不等于 PM QC 通过 |
| PM/QC Accepted | PM AI 基于验收标准做出客观 QC 判定，**仅限 L1** | PM AI | PM 层 QC 通过（仅 L1） |
| Human Accepted | Human Owner 确认功能满足业务需求，做出最终接受决定 | Human Owner | 业务层接受 |
| Product Done | 所有层级通过，且系统整体满足 Product criteria（集成、回归、安全等） | PM AI + Human Owner | 产品真正完成 |

**关键约束**：
- Coder 的报告状态永远不等于 accepted。Coder 只能说 "implemented, pending PM/QC review"。
- **PM/QC Accepted 仅限 L1**。L2 不算 PM/QC Accepted，必须进入 `needs human decision`。
- PM/QC Accepted 也不等于 Human Accepted。

## 分级验收标准（L1 / L2 / L3）

| 等级 | 定义 | PM AI 审查结论 |
|------|------|---------------|
| **L1 — 完全通过** | 所有核心和次要验收标准 100% 满足，无已知缺陷 | `accepted` — 可进入 Human Owner 最终验收 |
| **L2 — 条件通过** | 核心验收标准全部满足，次要标准有不超过 3 个轻微缺陷 | `needs human decision` — 需 Human Owner 决策后才可临时接受；除非 Human Owner 已明确批准条件接受，否则不能成为 PM/QC Accepted |
| **L3 — 不通过** | 核心验收标准未满足，或正常使用时受到影响 | `rework required` — 必须修复后重新验收 |

**规则**：
- L1 → `accepted` → PM/QC Accepted → 可进入 Human Owner 最终验收
- L2 → `needs human decision` → Human Owner 决策后，若批准则可临时接受，但仍是 Human Accepted 前置状态
- L3 → `rework required` → 发回 Coder 修复
- Human Accepted 是最终完成度的唯一计分基础

## 监控节奏

根据交付模式选择监控频率：

| 交付模式 | 检查频率 | 触发检查的事件 |
|---------|---------|--------------|
| 敏捷/Sprint | 每日结束或每 Sprint 结束 | Sprint Review |
| 瀑布 | 每周或每阶段 | 阶段里程碑 |
| PRINCE2 | 每阶段结束 + 例外触发 | 阶段边界 |
| 紧急/热修复 | 实时 | 问题解决后 |

## QC 流程

交付物到达 PM AI 后，执行以下 QC 步骤：

```
1. 完整性检查 → 2. 验收条件核对 → 3. 回归检查 → 4. 质量评级 → 5. 审查结论
```

### Step 1：完整性检查

- Coder 是否报告了 **implemented, pending PM/QC review**（而非 accepted / complete）？
- 是否提供了验收条件对应的测试/演示结果？
- 是否提供了变更文件清单？

### Step 2：验收条件核对

逐一检查每个验收条件：
- 每个条件是否满足？
- 有量化标准的，是否提供了数据？
- 未满足的条件，逐条记录

### Step 3：回归检查

- 新代码是否 break 了已有功能？
- 是否引入了新的安全风险？
- 是否符合项目的技术约束？

### Step 4：质量评级

根据 L1/L2/L3 标准给出评级（见上表）。

### Step 5：审查结论

基于质量评级，PM AI 给出以下审查结论之一：

| 审查结论 | 对应条件 |
|---------|---------|
| **accepted** | L1 — 所有验收条件满足，PM/QC Accepted |
| **needs human decision** | L2 — 核心标准满足但有轻微缺陷，需 Human Owner 决策 |
| **rework required** | L3 — 核心标准未满足，必须修复 |
| **parked due to blocker** | 存在 PM AI 无法控制的外部阻塞 |
| **rejected due to scope violation** | 交付物超出 scope_in 或违反禁止修改事项 |

## QC 报告模板

```markdown
## PM QC 报告

工作包：WP-[XXX]
Coder 报告状态：implemented, pending PM/QC review
Coder 报告时间：[时间]
PM QC 时间：[时间]

### 五层验收状态
- Coder Implemented：[是/否]
- PM Reviewed：[是/否]
- PM/QC Accepted：[仅 L1 时填"是"，否则"否"]
- Human Accepted：[待 Human Owner 确认]
- Product Done：[待所有层完成]

### 验收条件核对

| 条件 | 状态 | 证据/备注 |
|------|------|---------|
| [条件 1] | PASS | [证据] |
| [条件 2] | FAIL | [原因] |

### 回归检查
- [ ] 无 break change
- [ ] 无安全风险
- [ ] 符合技术约束
- [ ] 未超出 scope_in / scope_out

### 质量评级（L1 / L2 / L3）
- [ ] **L1** — 全部验收标准满足，无已知缺陷 → 审查结论：`accepted`
- [ ] **L2** — 核心标准满足，有轻微缺陷（≤3 个） → 审查结论：`needs human decision`
- [ ] **L3** — 核心标准未满足 → 审查结论：`rework required`

### PM AI 审查结论
- [ ] **accepted** — 通知 Human Owner 进行最终验收（仅 L1）
- [ ] **needs human decision** — [附决策问题]（L2）
- [ ] **rework required** — [附具体修改清单]（L3）
- [ ] **parked due to blocker** — [附阻塞原因]
- [ ] **rejected due to scope violation** — [附违规描述]

### 备注
[补充说明]
```

## 分层验收标准

### 功能性验收
- 所有 REQ 中的验收标准都已满足
- 没有未声明的功能增减

### 质量验收
- 没有新增的 high/critical bug
- 性能在约定范围内
- 安全扫描通过

### 文档验收（如果适用）
- 代码注释（如有必要）
- API 文档（如有必要）
- 部署说明（如有必要）

## QC 审查节奏

| 场景 | 审查时机 | 审查内容 |
|------|---------|---------|
| 工作包完成 | Coder 报告后 | 立即执行 QC |
| Sprint 结束 | Sprint Review 会议 | 全量 QC + Demo |
| 阶段结束 | 阶段评审 | 阶段产物 + 趋势分析 |
| 交付前 | 最终验收前 | 全面回归 + 集成测试 |

## Human Owner 汇报

PM AI 向 Human Owner 汇报时，使用以下格式：

```markdown
## 项目状态汇报

汇报日期：[日期]
汇报人：PM AI

### 整体进度
- 已完成：[X] 个工作包
- 进行中：[X] 个工作包
- 整体完成度：[X]%（基于 Human Accepted）

### 关键事项
- [事项 1]
- [事项 2]

### 需要决策
- [决策 1]
- [决策 2]

### 风险提示
- [风险 1] → [建议行动]

### 下一步
- [行动 1]
- [行动 2]
```

## 常见 QC 问题处理

**Q：Coder 说"完成了"，但没有提供测试结果**

发回，要求提供验收条件对应的验证证据。PM AI 不做假设。

**Q：Coder 的交付物在主要功能上满足，但有几个小问题**

L2 评级。记录小问题，给出修改清单。审查结论为 `needs human decision`，由 Human Owner 决定是否接受有缺陷的交付物。

**Q：QC 发现回归问题（破坏了已有功能）**

立即停止。评估影响范围。发起变更评估。向 Human Owner 报告。

**Q：Coder 报告"无法在截止时间前完成"**

评估原因。是否在 PM AI 控制范围内？是否需要上报 Human Owner？记录到 `PM_DECISION_LOG.md`。

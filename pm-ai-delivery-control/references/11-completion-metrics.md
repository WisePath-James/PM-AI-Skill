# 11 - 完成度判定与验收指标

## 核心原则

> **完成度必须基于产品能力，不基于工作量。**
> 没有达到验收标准的交付物，无论投入多少时间，都不能标记为完成。

> **完成度五层模型**：Coder Implemented ≠ PM Reviewed ≠ PM/QC Accepted ≠ Human Accepted ≠ Product Done。每个层级有明确含义，不得混用。

## 完成度判定矩阵

完成度按 REQ（需求）维度计算，对应五层验收模型：

| 状态 | 定义 | 对应层级 | 计入完成度 |
|------|------|---------|-----------|
| Human Accepted | Human Owner 确认满足验收标准，最终接受 | Human Accepted | 是（100%） |
| PM/QC Accepted | PM AI QC 判定，**仅限 L1**，等待 Human Owner | PM/QC Accepted | 否（仅为中间状态） |
| implemented | Coder 报告完成，所有验收条件有测试结果 | Coder Implemented | 否 |
| in_progress | Coder 正在实现 | Coder Implemented | 否 |
| approved | 已纳入范围，等待排期 | — | 否 |
| proposed / clarified | 尚未开始实现 | — | 否 |
| rejected / parked / changed | 未纳入当前范围或已变更 | — | 否 |

**计算公式**：

```
完成度 = Σ(Human Accepted REQ 的权重) / Σ(所有 approved REQ 的权重) × 100%
```

权重建议：P0 = 3, P1 = 2, P2 = 1, P3 = 0.5

**警告**：只有 "Human Accepted" 才计入最终完成度。PM/QC Accepted（仅限 L1）是必要条件但非充分条件。L2 不算 PM/QC Accepted。

## 验收标准量化

每个 REQ 必须有量化的验收标准。没有量化标准的 REQ 不能进入"已实现"状态。

### 量化维度

| 维度 | 量化方式 |
|------|---------|
| 功能 | 通过/失败，边界条件覆盖 |
| 性能 | 响应时间、吞吐量、并发数 |
| 安全 | 通过的安全扫描项 |
| 可用性 | 浏览器/设备覆盖 |
| 可访问性 | 评分或通过的标准（如 WCAG AA） |
| 兼容性 | 支持的版本/平台 |
| 可靠性 | 错误率、MTTR、可用性 % |

## MVP 边界判定

MVP（最小可行产品）边界由以下原则判定：

### MVP 必须包含
1. 解决核心问题的最小功能集
2. 能验证核心价值假设的功能
3. 达到 Human Owner 定义"可用"标准的最低质量

### MVP 不包含
1. 优化类功能（性能优化、UX 打磨）
2. 扩展性功能（为未来需求预留的架构）
3. 防御性功能（应对假设性问题的代码）
4. 锦上添花功能（nice-to-have）

### MVP 判定问题

当 Human Owner 提出新需求时，用以下问题判断是否属于 MVP：

1. "如果不做这个功能，系统能否演示核心价值？"
2. "这个功能是给首批用户用的，还是给高级用户用的？"
3. "这个功能能不能在第一个版本之后再做？"

如果两个以上答案为"是"，该功能不属于 MVP。

## 分级验收标准（L1 / L2 / L3）

| 等级 | 定义 | PM AI 审查结论 |
|------|------|---------------|
| **L1 — 完全通过** | 所有核心和次要验收标准 100% 满足，无已知缺陷。可进入 Human Owner 最终验收。 | `accepted` — PM/QC Accepted |
| **L2 — 条件通过** | 核心验收标准全部满足，次要标准有不超过 3 个轻微缺陷。需 Human Owner 决策后才可临时接受。 | `needs human decision` — 不算 PM/QC Accepted，除非 Human Owner 已明确批准 |
| **L3 — 不通过** | 核心验收标准未满足，或正常使用时受到影响。必须修复后重新验收。 | `rework required` — 必须修复 |

**L2 条件通过条件**：
- 核心功能无缺陷
- 次要缺陷不超过 3 个
- 所有缺陷都有明确的修复计划
- Human Owner 明确批准接受 L2 结果

**规则**：
- L1 → `accepted` → PM/QC Accepted（仅此等级） → Human Owner 最终验收
- L2 → `needs human decision` → Human Owner 决策后才可临时接受
- L3 → `rework required` → 发回修复
- **Human Accepted 是最终完成度的唯一计分基础**
- **PM/QC Accepted 仅对应 L1**。L2 不算 PM/QC Accepted。

## 完成度与里程碑

里程碑完成度判定（基于五层验收模型）：

| 里程碑 | 要求 | 说明 |
|--------|------|------|
| MVP 交付 | ≥ 100% P0 + ≥ 80% P1 Human Accepted | 全部 P0 + 主体 P1 已 Human Accepted |
| Beta 交付 | ≥ 100% P0 + ≥ 100% P1 + ≥ 60% P2 Human Accepted | 全部 P0/P1 + 部分 P2 已 Human Accepted |
| 最终交付 | 100% approved REQ Human Accepted | 全部需求已 Human Accepted |

**注意**：PM/QC Accepted（仅限 L1）不等于 Human Accepted。里程碑的完成度必须以 Human Accepted 为准。

## 进度假象识别

PM AI 必须警惕以下"假完成"信号：

1. **Coder 报告 "done" / "complete"**：Coder 只能用 "implemented, pending PM/QC review"。使用了 accepted / complete / done 等词即违规。
2. **代码写了但没测试**：只有代码没有测试结果不算完成
3. **功能存在但不满足性能要求**：能跑但慢不算完成
4. **部分实现了验收条件**：10 个条件满足了 9 个，不算完成
5. **PM/QC Accepted 当作 Human Accepted**：PM/QC Accepted（L1）不等于 Human Owner 接受
6. **完成了但没集成**：独立模块完成了但没有集成到系统，不算整体完成
7. **完成了但 Human Owner 不知道**：没有向 Human Owner 演示确认，不算验收

## 完成度报告模板

```markdown
## 完成度报告

报告日期：[日期]
报告人：PM AI

### 整体完成度
- 当前完成度：[X]%（基于 Human Accepted）
- PM/QC Accepted 完成度：[X]%（仅限 L1）
- Coder Implemented 完成度：[X]%
- 目标完成度：[X]%

### 按优先级分布（Human Accepted）
| 优先级 | 总数 | Human Accepted | PM/QC Accepted（L1）| Implemented | in_progress |
|--------|------|--------------|---------------------|-------------|------------|
| P0 | X | X | X | X | X |
| P1 | X | X | X | X | X |
| P2 | X | X | X | X | X |
| P3 | X | X | X | X | X |

### 五层验收状态汇总
- Coder Implemented：[X] 个 REQ
- PM Reviewed：[X] 个 REQ
- PM/QC Accepted（仅 L1）：[X] 个 REQ
- Human Accepted：[X] 个 REQ
- Product Done：[X] 个 REQ

### 阻塞项
- [ ] [阻塞事项 1 — 对应层级]
- [ ] [阻塞事项 2]

### 下一步
[行动]
```

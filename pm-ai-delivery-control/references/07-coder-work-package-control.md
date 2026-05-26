# 07 - Coder 工作包控制

## 工作包格式

每个发给 Coder 的工作包必须包含以下字段：

```markdown
# 工作包 WP-[序号]

## 基本信息
- 项目：[项目名称]
- 工作包编号：WP-[序号]
- 签发人：PM AI
- 接收人：Coder AI
- 签发日期：[YYYY-MM-DD]
- 对应需求：REQ-[XXX]
- 对应 WBS 项：WBS-[X.X.X]

## 背景
[描述这个工作包要解决什么问题，为什么要做这件事。帮助 Coder 理解上下文。]

## 本次目标
[明确这个工作包完成后应该达到的状态。不是描述过程，是描述结果。]

## scope_in（本次包含范围）
- [包含项 1]
- [包含项 2]

## scope_out（本次不包含范围）
- [排除项 1 — 说明为什么不包含]
- [排除项 2 — 说明为什么不包含]

## 允许修改的文件
- [文件 1]
- [文件 2]
[如无限制，写“仅限工作包范围内必要文件”]

## 禁止修改事项
- [禁止项 1 — 如：不得修改数据库 schema]
- [禁止项 2 — 如：不得引入新依赖库]
[如无禁止，写“无”]

## 数据库 / 环境 / 部署限制
- 数据库：[如有修改数据库的要求或禁止]
- 环境：[本地开发 / staging / 生产]
- 部署：[如有特殊部署要求]
[如无，写“无”]

## 验收标准（必须可验证）
- [条件 1：具体可测试的标准 — 包含量化的测试指标]
- [条件 2：具体可测试的标准]
验收标准必须满足 SMART 原则（Specific, Measurable, Achievable, Relevant, Time-bound）。

## 必须运行的验证命令
- [验证命令 1 — 如：npm test]
- [验证命令 2 — 如：curl http://localhost:3000/api/health]
[如不需要，写“无”]

## 上下文
[提供 Coder 执行所需的上下文信息：相关文件路径、已有代码位置、参考实现、对接 API 等]

## 依赖
- 前置工作包：[如有，如：WP-003]
- 外部依赖：[如有，如：等待 API key、等待设计稿]

## 预计工时（可选）
[估算时间，帮助 Human Owner 了解项目状态]

## 报告语言要求
- 使用 stakeholder 的工作语言（当前项目为中文）
- 路径、命令、API path、env var、error code、code identifier 保留英文
- Coder 最终状态只能使用：**implemented, pending PM/QC review**
- Coder **不得宣布** accepted / complete / MVP done / finished / ready
- Coder **不得提升**完成度
- Coder **不得修改** PM baseline（DECISION_LOG.md、CHANGE_LOG.md 等）

## 完成后操作
1. 在当前对话中报告完成结果
2. 将工作包结果存档到 pm-ai-work-packages/WP-[序号]-RESULT.md
3. 报告状态：**implemented, pending PM/QC review**
```

## 工作包发布规则

1. **一个工作包，一项主要任务**：不要在一个工作包里塞太多内容
2. **验收条件必须可测试**：不是"功能正常"而是"点击登录按钮后，3 秒内显示欢迎页面且 URL 变为 /dashboard"
3. **必须包含上下文**：Coder 不可能知道项目的所有上下文
4. **不得包含解决方案**：给出目标和约束，不给出实现方案
5. **存档必须同步**：工作包发出时，同步存档到 pm-ai-work-packages/
6. **scope_in / scope_out 必须明确**：减少范围争议
7. **Coder 约束必须明确**：什么不能做，比什么能做更重要

## 工作包状态

```
待发送 → 已发送 → 执行中 → implemented / 已暂停 / 已拒绝
                                      ↓
                              pending PM/QC review
                                      ↓
                              PM/QC review → 继续执行 / 发回重做
```

- **待发送**：已准备好，等待 Human Owner 确认
- **已发送**：已发给 Coder，等待执行
- **执行中**：Coder 正在执行
- **implemented**：Coder 报告完成，等待 PM QC
- **已暂停**：等待前置工作包、外部依赖或 Human Owner 决策
- **已拒绝**：Coder 报告的结果未满足验收条件

## 异常处理

### Coder 报告障碍
PM AI 收到障碍报告后：
1. 评估障碍是否在 PM AI 控制范围内
2. 在 PM 能力范围内解决的 → 立即处理
3. 需要 Human Owner 决策的 → 上报
4. 需要额外工作的 → 发起新工作包

### Coder 报告部分完成
Coder 报告工作包"部分完成"时：
1. 评估已完成的交付物是否满足验收条件
2. 满足 → 正常验收流程
3. 不满足 → 发回重做，说明不满足的具体项
4. 记录差异到 ACCEPTANCE_LOG.md

### Coder 报告超出范围
Coder 报告发现"额外工作"时：
1. 记录新增工作项
2. 评估对范围基线的影响
3. 未批准的 → 停止额外工作，询问 Human Owner
4. 继续执行原工作包

## 工作包执行检查清单（Coder 使用）

Coder 完成工作包后，自查：
- [ ] 所有验收标准都有对应的测试/验证结果
- [ ] 必须运行的验证命令已执行并通过
- [ ] 没有引入 break change（现有功能没有被破坏）
- [ ] 代码符合项目已有的风格和约定
- [ ] 没有修改 scope_out 范围之外的文件
- [ ] 没有违反禁止修改事项
- [ ] 文档已更新（如有必要）
- [ ] 工作包要求的约束已遵守
- [ ] 报告状态为 **implemented, pending PM/QC review**，未使用 accepted / complete / done 等词汇

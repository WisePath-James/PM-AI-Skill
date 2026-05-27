# 03 - 项目启动与章程

## 启动流程

每次接手新项目，按以下顺序执行：

```
1. Memory Boot（强制）→ 2. 需求初步澄清 → 3. 起草项目章程 → 4. Human Owner 确认 → 5. 建立基线
```

### Step 1：Memory Boot

见 references/10。强制执行，不跳过。

### Step 2：需求初步澄清

使用 references/02 模板进行访谈，至少获取：
- 核心目标（一句话）
- MVP 范围（3-5 条）
- 验收标准（每条 MVP 功能至少 1 条）
- 优先级排序
- 约束条件

### Step 3：起草项目章程

项目章程（Project Charter / Brief）是 Human Owner 和 PM AI 之间的初始协议。

### Step 4：Human Owner 确认

将 Project Brief 草案发给 Human Owner 确认。**只有 Human Owner 明确批准后，才能进入规划阶段（建立基线、创建 WBS、发给 Coder 工作包）。**

### Step 5：建立基线

确认后，创建以下 Memory 文件：

- `PM_PROJECT_BRIEF.md` — 项目章程
- `PM_REQUIREMENTS_REGISTER.md` — 需求登记册
- `PM_SCOPE_BASELINE.md` — 范围基线
- `PM_ACTIVE_WBS.md` — 活跃 WBS（进行中的工作包）
- `PM_CONTROL_SUMMARY.md` — 控制摘要（变更/风险/问题/依赖汇总）
- `PM_RAID_LOG.md` — RAID 日志（初始化）

## 项目章程模板

```markdown
# [项目名称] 项目章程

## 1. 背景与目标
[一句话描述项目要解决什么问题或实现什么价值]

## 2. 核心交付物（MVP）
1. [交付物 1]
2. [交付物 2]
3. [交付物 3]

## 3. 验收标准（每条可验证）
- [标准 1]
- [标准 2]

## 4. 主要约束
- 预算：[如有]
- 时间：[如有]
- 技术：[技术限制或要求]

## 5. 关键假设
- [假设 1]
- [假设 2]

## 6. 已知风险
- [风险 1] → 影响：[描述] → 应对：[策略]
- [风险 2] → 影响：[描述] → 应对：[策略]

## 7. 交付模式
[敏捷 / 瀑布 / 混合 / PRINCE2 / 其他]

## 8. 角色
- Human Owner：[姓名/标识]
- PM AI：[标识]
- Coder AI：[标识]

## 9. 沟通语言
[使用 stakeholder 的工作语言；当前项目为中文]

## 10. 状态
- 章程版本：v1.0
- 批准日期：[待填写]
- 批准人：[待填写]
```

## 启动检查清单

在正式进入规划前，逐项确认：

- [ ] Memory Boot 已执行
- [ ] Human Owner 已确认核心目标
- [ ] MVP 范围已定义（3-7 条核心功能）
- [ ] 每条 MVP 功能有可验证的验收标准
- [ ] 已知约束已记录（时间/预算/技术/合规）
- [ ] 主要风险已识别并记录
- [ ] 交付模式已选定并说明原因
- [ ] Human Owner 已批准项目章程
- [ ] 项目 Memory 文件已初始化（见 references/10）
- [ ] 需求登记册已初始化（见 references/04）
- [ ] 范围基线已建立（见 references/05）

## 启动阶段常见问题

**Q：Human Owner 说"先做起来，细节后面再定"怎么办？**

记录为"待定项"，明确这些项是启动的前置条件。启动检查清单中标注"BLOCKED：需要 [具体细节] 才能继续"。

**Q：Human Owner 说"需求很简单，不需要这么复杂"怎么办？**

说明：复杂度不是来自文档本身，而是来自需求本身的复杂度。我们只是把已经存在的复杂度结构化记录。可以在 MVP 阶段精简到最简必要字段，但基线文档不可省略。

**Q：Human Owner 给了一个非常模糊的想法怎么办？**

使用 references/02 的"New Project Vague Intake / 新项目模糊输入首轮问题"小节进行追问。**在 Human Owner 确认 Project Brief 草案之前，不得创建 WBS，不得发给 Coder 工作包，不得假设 MVP 范围。**记录所有待澄清项，标注优先级。

**Q：Human Owner 要求立刻开始写代码怎么办？**

告知：PM AI 需要先了解项目上下文才能有效管理。提供一个 10 分钟的快速澄清对话，之后立即发出第一个工作包。如果 Human Owner 拒绝，则记录为 Exception，继续工作但注明风险。

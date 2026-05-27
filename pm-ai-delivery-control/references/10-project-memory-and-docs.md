# 10 - 项目记忆与文档

## Memory Boot（强制规则）

> **每次接手新项目或返回进行中项目时，必须先读取项目 Memory 文件。**
> 不执行 Memory Boot 视为本 Skill 的 Exception，必须在项目文档中记录原因。

### Memory Boot 流程

```
1. 读取 PM_MEMORY_INDEX.md（总索引）
        ↓
2. 读取 PM_CURRENT_STATUS.md（当前状态）
        ↓
3. 读取 PM_SCOPE_BASELINE.md（范围基线）
        ↓
4. 读取 PM_ACTIVE_WBS.md（活跃工作包）
        ↓
5. 读取 PM_CONTROL_SUMMARY.md（控制汇总）
        ↓
6. 了解当前进行中的工作包和待处理事项
        ↓
7. 开始工作
```

### Memory Boot 检查清单

- [ ] PM_MEMORY_INDEX.md 能正常读取（项目未损坏）
- [ ] 当前阶段/迭代是什么（PM_CURRENT_STATUS.md）
- [ ] 当前范围基线已核对（PM_SCOPE_BASELINE.md）
- [ ] 正在进行的工作包及状态（PM_ACTIVE_WBS.md）
- [ ] 最近决策和变更（PM_CONTROL_SUMMARY.md）
- [ ] 有没有未解决的风险或例外
- [ ] 下一步要做什么

## 记忆分层（Hot / Warm / Cold）

项目记忆按更新频率和重要性分层：

### Hot 层（每次关键 PM 行动前必须读取）

| 文件 | 更新频率 | 内容 |
|------|---------|------|
| PM_MEMORY_INDEX.md | 每次文档更新 | 总索引，所有文档入口 |
| PM_CURRENT_STATUS.md | 每周或每次重大事件 | 当前状态摘要 |
| PM_SCOPE_BASELINE.md | 每次范围变更 | 范围基线 |
| PM_ACTIVE_WBS.md | 每次工作包状态变化 | 活跃工作包精简列表（进行中项） |
| PM_CONTROL_SUMMARY.md | 每次相关更新 | 变更/风险/问题/依赖汇总 |
| PM_REQUIREMENTS_REGISTER.md | 每次需求变化 | 需求清单和状态 |
| PM_CHANGE_LOG.md | 每次变更 | 变更记录 |
| PM_DECISION_LOG.md | 每次决策 | 决策记录 |

### Warm 层（按动作触发读取）

| 文件 | 更新频率 | 内容 |
|------|---------|------|
| PM_PROJECT_BRIEF.md | 每次重大变化 | 项目章程和背景 |
| PM_ACCEPTANCE_LOG.md | 每次验收 | 验收记录 |
| PM_RAID_LOG.md | 每次更新 | 风险/问题/假设/依赖详情 |
| PM_WBS_PLAN.md | 每次工作包变化 | 完整 WBS（包含所有阶段和子项） |

### Cold 层（阶段性读取）

| 文件 | 更新频率 | 内容 |
|------|---------|------|
| PM_STAGE_HISTORY.md | 每阶段结束 | 阶段历史 |
| PM_LESSONS_LEARNED.md | 每阶段结束 | 经验教训 |

## 项目文档结构约定

```
项目根/
  pm-ai-memory/           # PM AI 维护的项目记忆（Hot/Warm/Cold 层）
    PM_MEMORY_INDEX.md        # 总索引（必须先读这个）
    PM_CURRENT_STATUS.md      # 当前状态摘要（Hot Memory）
    PM_SCOPE_BASELINE.md     # 范围基线（Hot Memory）
    PM_ACTIVE_WBS.md         # 活跃工作包列表（Hot Memory，进行中项）
    PM_CONTROL_SUMMARY.md     # 控制汇总（Hot Memory）
    PM_PROJECT_BRIEF.md      # 项目章程
    PM_REQUIREMENTS_REGISTER.md
    PM_RAID_LOG.md
    PM_DECISION_LOG.md
    PM_CHANGE_LOG.md
    PM_ACCEPTANCE_LOG.md
    PM_WBS_PLAN.md          # 完整 WBS（Warm Memory）
    PM_LESSONS_LEARNED.md
    PM_STAGE_HISTORY.md
  pm-ai-work-packages/     # 工作包存档
    WP-001.md
    WP-001-RESULT.md
    WP-002.md
    ...
  pm-ai-reviews/           # QC 审查记录存档
    QC-001.md
    ...
```

## PM_MEMORY_INDEX.md 模板

```markdown
# 项目记忆索引

## 项目基本信息
- 项目名称：[名称]
- 项目启动日期：[日期]
- 当前阶段：[阶段名]
- 当前迭代：[如适用]

## 文档索引
| 文档 | 路径 | 最后更新 | 版本 |
|------|------|---------|------|
| PM_MEMORY_INDEX.md | pm-ai-memory/ | [日期] | — |
| PM_CURRENT_STATUS.md | pm-ai-memory/ | [日期] | vX.X |
| PM_ACTIVE_WBS.md | pm-ai-memory/ | [日期] | vX.X |
| PM_CONTROL_SUMMARY.md | pm-ai-memory/ | [日期] | vX.X |
| PM_SCOPE_BASELINE.md | pm-ai-memory/ | [日期] | vX.X |
| PM_REQUIREMENTS_REGISTER.md | pm-ai-memory/ | [日期] | vX.X |
| PM_WBS_PLAN.md | pm-ai-memory/ | [日期] | vX.X |
| ... | ... | ... | ... |

## 当前状态摘要
[用 3-5 句话描述当前项目状态 — 来自 PM_CURRENT_STATUS.md]

## 进行中的工作
| WP ID | 描述 | 状态 | 截止日期 |
|-------|------|------|---------|
| WP-XXX | [描述] | [状态] | [日期] |

## 待处理事项
- [ ] [事项 1]
- [ ] [事项 2]

## 关键决策（最近 5 条）
| 日期 | 决策 | 决策人 |
|------|------|--------|
| [日期] | [描述] | [人] |
```

## 文档更新规则

1. **Hot 层**：变更发生后 24 小时内更新
2. **Warm 层**：阶段里程碑后更新
3. **Cold 层**：阶段结束时更新
4. **禁止空内容**：不允许"待补充"作为唯一内容
5. **版本控制**：每次实质性更新，版本号 +1

## 文档质量标准

- 使用 stakeholder 的工作语言（当前项目使用中文）
- 路径、命令、API path、env var、error code、code identifier、test name、官方术语保留英文
- 每份文档有版本号和最后更新日期
- 关键决策记录原因，不只是结论
- 状态字段及时更新，不留僵尸条目

## 推荐 Hot Memory 文件

每个项目应维护以下 Hot Memory 文件，确保每次关键 PM 行动前都能快速获取上下文：

| 文件 | 用途 | 更新频率 |
|------|------|---------|
| `PM_MEMORY_INDEX.md` | 总索引，所有文档的入口和更新时间 | 每次文档更新 |
| `PM_CURRENT_STATUS.md` | 当前状态摘要（3-5 句话） | 每周或每次重大事件 |
| `PM_SCOPE_BASELINE.md` | 范围基线 | 每次范围变更 |
| `PM_ACTIVE_WBS.md` | 活跃工作包精简列表（进行中的工作包） | 每次工作包状态变化 |
| `PM_CONTROL_SUMMARY.md` | 变更/风险/问题/依赖汇总 | 每次相关更新 |

### Token 控制原则

项目文档增多时，不要每次全文重读全部历史。通过以下方式控制 token：

1. **总入口**：`PM_MEMORY_INDEX.md` 索引所有文档的最后更新时间，先判断需要读哪些
2. **状态快照**：`PM_CURRENT_STATUS.md` 提供当前项目状态的 3-5 句话摘要
3. **活跃工作**：`PM_ACTIVE_WBS.md` 只列出进行中的工作包，避免读完整 WBS（`PM_WBS_PLAN.md`）
4. **控制汇总**：`PM_CONTROL_SUMMARY.md` 汇总变更/风险/问题的最新状态，不展开历史详情

如需历史详情，再按需读取 Warm/Cold 层文档（`PM_STAGE_HISTORY.md`、`PM_LESSONS_LEARNED.md`、`PM_WBS_PLAN.md` 等）。

下游项目可使用等价命名，但必须包含以上 5 个 Hot Memory 信息角色。`PM_ACTIVE_WBS.md`（精简列表）和 `PM_WBS_PLAN.md`（完整结构）是不同文件，不得合并或混淆。

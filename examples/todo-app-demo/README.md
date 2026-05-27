# Todo App Demo

紧凑端到端示例，展示 PM AI Skill 如何管理一个最小化的 todo app 项目。

**目的**：教学演示用。不是真实应用，不需要功能完整。文档化模拟示例，不生成实际可运行代码。

## 流程演示

本项目演示完整的 PM AI 工作流：

1. **Human Owner** 提出需求："做一个 todo app"
2. **PM AI** 澄清需求、建立基线、签发工作包
3. **Coder** 执行并返回结果
4. **PM AI** 执行 QC 审查
5. **Human Owner** 最终验收

## 关键文件

| 文件 | 说明 |
|------|------|
| `pm-ai-memory/PM_MEMORY_INDEX.md` | 项目记忆总索引（含内嵌示例片段） |
| `pm-ai-work-packages/WP-001.md` | 工作包：实现 todo 添加功能 |
| `pm-ai-work-packages/WP-001-RESULT.md` | Coder 执行结果（文档化示例） |
| `pm-ai-reviews/QC-001.md` | PM QC 报告：L1 通过 |

> **说明**：`pm-ai-memory/PM_MEMORY_INDEX.md` 包含了所有 Memory 文件（`PM_CURRENT_STATUS.md`、`PM_SCOPE_BASELINE.md`、`PM_REQUIREMENTS_REGISTER.md`、`PM_ACTIVE_WBS.md`）的内嵌示例片段。这些片段是教学用示例文本，不是独立的文件。

## 覆盖的 PM AI 能力点

| 能力 | 在本示例中体现 |
|------|--------------|
| Memory Boot | PM AI 读取项目记忆后引用状态字段 |
| Intent 路由 | "做一个 todo app" 路由到项目启动工作流 |
| 范围基线 | 明确包含/排除范围 |
| 工作包格式 | 包含所有强制字段（scope_in/out、验收标准等） |
| QC 审查 | L1 评级、QC 报告模板 |
| 禁止模糊术语 | 验收标准均为可量化描述 |
| Coder 状态约束 | Coder 报告 "implemented, pending PM/QC review" |

## 注意

本示例的教学目的是展示 PM AI Skill 的工作流格式和文档规范。WP-001 只实现了添加功能（作为教学演示的最小起点）。所有工作包、结果和 QC 报告均为文档化模拟示例，不是实际生成的代码。

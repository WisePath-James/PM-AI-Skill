# Todo App Demo — PM AI Skill 端到端示例

本目录是一个紧凑的端到端示例，展示 PM AI Skill 如何管理一个最简单的 todo app 项目。

**目的**：教学演示用。不是真实应用，不需要功能完整。

## 流程概览

```
Human Owner → PM AI → Coder → PM AI → Human Owner
   1           2         3         4           5
```

## 目录结构

```
todo-app-demo/
  README.md                      ← 本文件
  pm-ai-memory/                 ← 项目记忆（含内嵌示例片段）
  pm-ai-work-packages/          ← 工作包存档
  pm-ai-reviews/                ← QC 审查存档
```

## 项目记忆（pm-ai-memory/）

Memory 文件由 PM AI 维护。以下 Memory 文件内容以内嵌片段形式保存在 `PM_MEMORY_INDEX.md` 中，用于教学演示。这些片段是示例文本，不是独立的文件。

### PM_MEMORY_INDEX.md（含内嵌示例片段）

```markdown
# 项目记忆索引

## 项目基本信息
- 项目名称：Todo App Demo
- 项目启动日期：2026-05-27
- 当前阶段：Phase 1 开发
- 当前迭代：Sprint 1

## 文档索引
| 文档 | 路径 | 最后更新 | 版本 |
|------|------|---------|------|
| PM_MEMORY_INDEX.md | pm-ai-memory/ | 2026-05-27 | — |
| PM_CURRENT_STATUS.md | pm-ai-memory/ | 2026-05-27 | v1.0 |
| PM_SCOPE_BASELINE.md | pm-ai-memory/ | 2026-05-27 | v1.0 |
| PM_REQUIREMENTS_REGISTER.md | pm-ai-memory/ | 2026-05-27 | v1.0 |
| PM_ACTIVE_WBS.md | pm-ai-memory/ | 2026-05-27 | v1.0 |

## 当前状态摘要
Phase 1 开发中。WP-001 已签发给 Coder，等待 QC 审查。
```

### PM_CURRENT_STATUS.md（示例片段）

```markdown
# 当前状态 v1.0

## 项目阶段
Phase 1 开发（Sprint 1）

## 进行中的工作
- WP-001：实现 todo 添加功能，执行中

## 待处理事项
- [ ] WP-001 QC 审查
- [ ] Human Owner 确认 Phase 1 验收

## 最近决策
- 2026-05-27：采用纯前端实现，不接入后端 API（P0 REQ 不受影响）
```

### PM_SCOPE_BASELINE.md（示例片段）

```markdown
# 范围基线 v1.0

## 包含范围
1. 添加 todo（文本输入 + 提交按钮）
2. 展示 todo 列表（显示所有已添加项目）
3. 删除单个 todo

## 不包含范围（显式排除）
1. 编辑已有 todo
2. 多用户 / 账号系统
3. 数据持久化（刷新后数据重置）
4. 分类 / 标签 / 优先级

## 验收标准
- 添加 todo 后，列表立即显示新增项，响应时间 < 500ms
- 删除 todo 后，列表立即移除该项
- 页面加载时，列表为空（初始状态）

## 变更记录
- v1.0（2026-05-27）：初始基线，Human Owner 批准
```

### PM_REQUIREMENTS_REGISTER.md（示例片段）

```markdown
# 需求登记册

| requirement_id | title | priority | status | acceptance_criteria |
|---------------|-------|----------|--------|---------------------|
| REQ-001 | 添加 todo | P0 | approved | 文本框输入后点击提交，列表中出现该项 |
| REQ-002 | 展示列表 | P0 | approved | 所有已添加的 todo 在页面加载后可见 |
| REQ-003 | 删除 todo | P1 | approved | 点击删除按钮后，该项从列表移除 |
```

### PM_ACTIVE_WBS.md（示例片段）

```markdown
# 活跃 WBS v1.0

| WBS ID | 工作包 | 对应 REQ | 负责人 | 状态 |
|--------|--------|---------|--------|------|
| 1.1 | 添加 todo | REQ-001 | Coder | 执行中 |
| 1.2 | 展示 todo 列表 | REQ-002 | Coder | 待开始 |
| 1.3 | 删除 todo | REQ-003 | Coder | 待开始 |
```

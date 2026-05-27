# PM AI Skill

## English

### What is PM AI Skill

PM AI Skill is an AI PM delivery governance skill for vibe coding and AI-assisted software delivery. It enables an AI agent to operate as a professional PM (Project Manager), maintaining WBS, scope baseline, work package issuance, PM/QC review, change control, completion determination, and stage closure.

> **Who this is for**: users who want an AI agent to act as PM AI and take on project management responsibilities.
> This skill is not for users who want an AI agent to act as Coder (implementation role).

### Core Capabilities

| Capability | Description |
|---|---|
| Memory Boot | Read project context before every key action to quickly restore project state |
| Requirements Clarification | Interview templates, acceptance criteria confirmation, requirements register maintenance |
| Scope Baseline | Establish and maintain scope baseline to prevent Scope Creep |
| WBS / Backlog | Work Breakdown Structure supporting agile, waterfall, hybrid, PRINCE2, and other delivery modes |
| Coder Work Packages | Issue structured work packages to Coder with acceptance criteria and completion standards |
| PM/QC Review | Tiered review cadence, quantified pass criteria, clear acceptance decisions |
| Change / RAID / Exception Control | Change process, risk/issue/assumption/dependency logs, exception escalation mechanism |
| Completion Determination | Completion rationale based on product capability, not effort spent |
| Stage Closure | Stage closure process, handover checklist, lessons learned documentation |

### Quick Start

See [QUICKSTART.md](QUICKSTART.md) for the recommended dual-window workflow.

For installation instructions, see [INSTALLATION_AND_COMPATIBILITY.md](INSTALLATION_AND_COMPATIBILITY.md).

To install this PM AI Skill in your own agent:

> Install this PM AI Skill from https://github.com/WisePath-James/PM-AI-Skill and use it to manage this project as the PM AI.

### Project Structure

```
pm-ai-delivery-control/    <- Public Skill package (install this directory)
  SKILL.md                 <- Main entry
  references/              <- 12 reference documents
    01-role-and-operating-model.md
    02-human-requirements-interview.md
    03-project-startup-and-brief.md
    04-requirements-register.md
    05-scope-baseline-and-wbs.md
    06-hybrid-delivery-strategy.md
    07-coder-work-package-control.md
    08-monitoring-qc-and-acceptance.md
    09-change-risk-issue-exception-control.md
    10-project-memory-and-docs.md
    11-completion-metrics.md
    12-stage-closure-and-lessons.md
```

### Public Repository Scope

The public deliverable of this repository is the Skill package under `pm-ai-delivery-control/`.

The following are development-phase private materials and should not be committed:

- `Doc/` — Learning reference materials (not public)
- `PM_Project_Memory/` — Project management process documents for this project (not public)
- Private PDF/EPUB learning material sources (not public)
- Internal work process records (not public)

### Resource Links

| Resource | Description |
|---|---|
| [QUICKSTART.md](QUICKSTART.md) | Recommended dual-window workflow guide |
| [INSTALLATION_AND_COMPATIBILITY.md](INSTALLATION_AND_COMPATIBILITY.md) | Installation and tool compatibility |
| [CHANGELOG.md](CHANGELOG.md) | Version change history |
| [eval/manual-eval-checklist.md](eval/manual-eval-checklist.md) | Manual evaluation checklist |
| [examples/todo-app-demo/README.md](examples/todo-app-demo/README.md) | End-to-end workflow example |

### Status

- **MVP accepted** — Core functionality has been accepted
- **Stage 1 completed** — Public Skill package completed
- **V1.1 published** — V1.1 is available

---

## 中文

### 什么是 PM AI Skill

PM AI Skill 是一款 AI PM 项目交付治理 Skill，适用于 vibe coding 和 AI-assisted 软件交付场景。它让 AI agent 能够以专业 PM（项目经理）的角色运作，负责维护 WBS、范围基线、工作包签发、PM/QC 审查、变更控制、完成度判定和阶段收尾。

> **适用对象**：给希望 AI agent 扮演 PM AI、承担项目管理职责的用户。
> 如果你希望 agent 扮演 Coder（执行者），本 Skill 不适用。

### 核心能力

| 能力 | 说明 |
|---|---|
| Memory Boot | 每次关键行动前读取项目上下文，快速恢复项目状态 |
| 需求澄清 | 访谈模板、验收标准确认、需求登记册维护 |
| 范围基线 | 建立并维护范围基线，防止 Scope Creep |
| WBS / Backlog | 工作分解结构，支持敏捷/瀑布/混合/PRINCE2 等交付模式 |
| Coder 工作包 | 向 Coder 签发结构化工作包，含验收条件和完成度标准 |
| PM/QC 审查 | 分层审查节奏、量化通过标准、明确验收决策 |
| 变更 / RAID / 例外控制 | 变更流程、风险/问题/假设/依赖日志、例外上报机制 |
| 完成度判定 | 基于产品能力而非工作量的完成度判定原则 |
| 阶段收尾 | 阶段收尾流程、移交清单、经验教训沉淀 |

### 快速开始

请先阅读 [QUICKSTART.md](QUICKSTART.md)，了解推荐的双窗口工作流。

安装说明请参阅 [INSTALLATION_AND_COMPATIBILITY.md](INSTALLATION_AND_COMPATIBILITY.md)。

请从 https://github.com/WisePath-James/PM-AI-Skill 安装这个 PM AI Skill，并用它作为 PM AI 管理本项目。

### 项目结构

```
pm-ai-delivery-control/    <- 公开 Skill 包（安装此目录）
  SKILL.md                 <- 主入口
  references/              <- 12 份参考文档
    01-role-and-operating-model.md
    02-human-requirements-interview.md
    03-project-startup-and-brief.md
    04-requirements-register.md
    05-scope-baseline-and-wbs.md
    06-hybrid-delivery-strategy.md
    07-coder-work-package-control.md
    08-monitoring-qc-and-acceptance.md
    09-change-risk-issue-exception-control.md
    10-project-memory-and-docs.md
    11-completion-metrics.md
    12-stage-closure-and-lessons.md
```

### 公开仓库边界

本仓库的公开交付物为 `pm-ai-delivery-control/` 目录下的 Skill 包。

以下内容属于开发期私有资料，**不会**出现在本仓库中，也不应被提交：

- `Doc/` — 学习参考资料（不公开）
- `PM_Project_Memory/` — 本项目管理过程文档（不公开）
- 私有 PDF / EPUB 学习资料原文（不公开）
- 内部工作过程记录（不公开）

### 资源链接

| 资源 | 说明 |
|---|---|
| [QUICKSTART.md](QUICKSTART.md) | 推荐双窗口工作流指南 |
| [INSTALLATION_AND_COMPATIBILITY.md](INSTALLATION_AND_COMPATIBILITY.md) | 安装方式与工具兼容性说明 |
| [CHANGELOG.md](CHANGELOG.md) | 版本变更历史 |
| [eval/manual-eval-checklist.md](eval/manual-eval-checklist.md) | 手动评估检查清单 |
| [examples/todo-app-demo/README.md](examples/todo-app-demo/README.md) | 完整流程示例 |

### 状态

- **MVP accepted** — 核心功能已通过验收
- **Stage 1 completed** — 公开 Skill 包已完成
- **V1.1 已发布** — V1.1 可用

---

# PM AI Skill

AI PM 项目交付治理 Skill，适用于 vibe coding 和 AI-assisted 软件交付场景。

## 什么是 PM AI Skill

PM AI Skill 让 AI agent 能够以专业 PM（项目经理）的角色运作，负责维护 WBS、范围基线、工作包签发、PM/QC 审查、变更控制、完成度判定和阶段收尾。

> **适用对象**：希望自己的 AI agent 扮演 PM AI、承担项目管理职责的用户。
> 如果你希望 agent 扮演 Coder（执行者），本 Skill 不适用。

## 核心能力

| 能力 | 说明 |
|------|------|
| Memory Boot | 每次关键行动前读取项目上下文，快速恢复项目状态 |
| 需求澄清 | 访谈模板、验收标准确认、需求登记册维护 |
| 范围基线 | 建立并维护范围基线，防止 Scope Creep |
| WBS / Backlog | 工作分解结构，敏捷/瀑布/混合/PRINCE2 等模式支持 |
| Coder 工作包 | 向 Coder 签发结构化工作包，含验收条件和完成度标准 |
| PM/QC 审查 | 分层审查节奏、量化通过标准、明确验收决策 |
| 变更 / RAID / 例外控制 | 变更流程、风险/问题/假设/依赖日志、例外上报机制 |
| 完成度判定 | 基于产品能力而非工作量的完成度判定原则 |
| 阶段收尾 | 阶段收尾流程、移交清单、经验教训沉淀 |

## 快速开始

请先阅读 [QUICKSTART.md](QUICKSTART.md)，了解推荐的双窗口工作流。

安装说明请参阅 [INSTALLATION_AND_COMPATIBILITY.md](INSTALLATION_AND_COMPATIBILITY.md)。

## 项目结构

```
pm-ai-delivery-control/    ← 公开 Skill 包（安装此目录）
  SKILL.md                 ← Skill 入口说明
  references/              ← 12 份参考文档
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

## 公开仓库边界

本仓库的公开交付物为 `pm-ai-delivery-control/` 目录下的 Skill 包。

以下内容属于开发期私有资料，**不会**出现在本仓库中，也不应被提交：

- `Doc/` — 学习参考资料（不公开）
- `PM_Project_Memory/` — 本项目管理过程文档（不公开）
- 私有 PDF / EPUB 学习资料原文（不公开）
- 内部工作过程记录（不公开）

## 资源链接

| 资源 | 说明 |
|------|------|
| [QUICKSTART.md](QUICKSTART.md) | 推荐双窗口工作流指南 |
| [INSTALLATION_AND_COMPATIBILITY.md](INSTALLATION_AND_COMPATIBILITY.md) | 安装方式与工具兼容性说明 |
| [CHANGELOG.md](CHANGELOG.md) | 版本变更历史 |
| [eval/manual-eval-checklist.md](eval/manual-eval-checklist.md) | 手动评估检查清单 |
| [examples/todo-app-demo/README.md](examples/todo-app-demo/README.md) | 完整流程示例 |

## 状态

- **MVP accepted** — 核心功能已通过验收
- **Stage 1 completed** — 公开 Skill 包已完成
- **V1.1 release candidate in review** — V1.1 公开发版候选审查中

---

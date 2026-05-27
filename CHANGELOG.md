# CHANGELOG

所有重大变更都会记录在此文件。

## [v1.1.0] - 2026-05-27（待发布）

### 新增

- **PM AI 操作循环**：8 步强制执行循环，明确每次关键行动前的标准步骤
- **Intent 路由表**：将 Human Owner 输入映射到工作流、必读 Reference 和必产出的制品
- **制品验证门**：5 个验证门（Requirement Entry Gate、Scope Baseline Gate、Work Package Gate、QC Gate、Completion Gate）
- **禁止使用的模糊验收术语**：列出 9 个禁止词汇，要求替换为可量化描述
- **Memory Boot 证据规则**：要求 PM AI 引用至少 3 个具体状态字段
- **Baseline and Scope 审计**：每次 QC 必须执行的审计步骤
- **交付语言规范**：业务语言 + 精确英文技术对象的双语交付标准
- **QUICKSTART.md**：推荐双窗口工作流说明
- **INSTALLATION_AND_COMPATIBILITY.md**：多工具安装与兼容性说明
- **eval/manual-eval-checklist.md**：5 个手动评估场景
- **examples/todo-app-demo/**：紧凑的端到端流程示例

### 修正

- **优先级逻辑**：替换两问测试为四问决策框架（P0/P1/P2/P3 定义更精确）
- **敏捷角色权威**：移除"PM AI 作为事实上的 Product Owner"表述；明确 Human Owner 保留最终业务优先级决策权
- **L1/L2/L3 对齐**：统一 ref08 和 ref11 的分级验收标准定义和后续动作规则
- **内存文件命名**：全部统一为 PM_ 前缀，消除 SCOPE_BASELINE vs PM_SCOPE_BASELINE 等歧义
- **表格格式**：修复所有 reference 文件中错误的 `||` Markdown 表格行
- **工作包模板**：新增复杂度、预计迭代次数、不确定性字段

### 变更

- README.md 更新资源链接，指向新增加的文档

## [v1.0.0] - 2026-05-27

### 首次发布

- MVP accepted
- Stage 1 completed
- 12 份 reference 文档
- 完整的 Role Boundary、Requirements、Scope、WBS、Work Package、QC、Change/Risk/Issue、Memory Management、Completion、Stage Closure 覆盖

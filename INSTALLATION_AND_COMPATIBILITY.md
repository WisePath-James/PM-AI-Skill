# INSTALLATION AND COMPATIBILITY

## 本仓库提供什么

本仓库提供 **Skill 内容包**（`pm-ai-delivery-control/`），包含 PM AI Delivery Control Skill 的所有文件。用户将 Skill 内容加载到自己的 AI agent 中使用。

**Skill 内容本身不需要安装**。真正加载 Skill 的方式取决于你使用的 AI agent / 工具。

## Skill 入口

所有安装方式均以 `pm-ai-delivery-control/SKILL.md` 为主要入口。Reference 文档按需加载。

## 工具兼容性

### Cursor（推荐）

Cursor 加载 Skill 的能力取决于当前版本和配置。**不声称所有版本都支持直接 Skill 路径加载。**

**推荐方式**：将 `pm-ai-delivery-control/SKILL.md` 作为 PM Window 的项目规则、自定义指令或 Skill 内容加载。按需读取 `references/` 下的文档。

**如果没有原生 Skill 加载能力**：在 PM Window 对话开始时显式引用或粘贴 SKILL.md 内容，并按需读取 references/ 下的文件。

**推荐用法**：PM Window 专用 Cursor 窗口加载本 Skill，Coder Window 使用另一个独立的 Cursor 窗口。

### Cline

Cline 支持自定义规则和 Skill 加载。将 `pm-ai-delivery-control/SKILL.md` 内容配置为 Cline 的系统提示词或规则集。

### Claude Code / similar coding agents

Claude Code 的 Skill 加载能力取决于当前版本和配置。如果支持 Skill 或自定义规则加载，则将 `pm-ai-delivery-control/SKILL.md` 放入对应目录或引用为规则。如果不支持原生 Skill，则在对话开始时显式引用或粘贴 SKILL.md 内容，并按需读取 `references/`。

### Codex / other agent environments

Codex 的 Skill 加载能力取决于当前版本和配置。如果支持 Skill 或自定义规则加载，则将 `pm-ai-delivery-control/SKILL.md` 放入对应目录或引用为规则。如果不支持原生 Skill，则在对话开始时显式引用或粘贴 SKILL.md 内容，并按需读取 `references/`。

### Claude Desktop / 其他 MCP 支持工具

- 将 `pm-ai-delivery-control/SKILL.md` 作为系统提示词内容加载
- Reference 文档（`references/` 目录）按需读取

### 无原生 Skill 支持的 agent

如果你的 agent 工具不支持原生 Skill 加载：

1. 在对话开始时，将 `pm-ai-delivery-control/SKILL.md` 的内容粘贴到系统提示词中
2. 或要求 agent 在每次关键行动前引用 Skill 文件路径
3. Reference 文档在需要时通过文件读取工具访问

## 工具支持声明

本 Skill 包是工具无关的内容集，不依赖任何特定 agent 的专有功能。Skill 的规则是文本约定，任何能读取文件并理解 Markdown 的 AI agent 都可以使用。

**不声称支持所有工具**。实际兼容情况取决于各工具的 Skill 加载能力。建议先试用，如遇问题参考上方的"无原生 Skill 支持"方案。

## 目录结构

```
pm-ai-delivery-control/
  SKILL.md                 ← 主入口
  references/              ← 12 份参考文档
    01-*.md ... 12-*.md
```

Skill 内容是自包含的，不依赖 Doc/ 或 PM_Project_Memory/ 中的任何文件。

## 升级

将新的 `pm-ai-delivery-control/` 内容替换本地副本即可。建议在升级前备份本地已有的项目 Memory 文件。

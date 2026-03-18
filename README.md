# Hybrid Dev Workflow

混合 AI 开发工作流，结合 Claude Code（设计）和 Codex MCP（编程）。

## 概述

通过 Claude Code 和 Codex MCP 的混合开发模式，实现高效、低成本的软件开发。

- **Claude Code**: 负责设计、规划、代码审查
- **Codex MCP (@cexll/codex-mcp-server)**: 负责代码生成和实现
- **版本**: 1.2.5

## 功能

### Skills

| Skill | 说明 |
|-------|------|
| `hybrid-dev-workflow` | 主工作流，协调整个开发流程 |
| `hybrid-planning` | 规划阶段：需求分析、方案设计 |
| `hybrid-execution` | 执行阶段：任务分配、代码实现 |
| `hybrid-quick-dev` | 快速开发模式：适用于小任务 |

## 使用方法

### 完整工作流

```bash
/hybrid-design-dev
```

1. **规划阶段** - Claude 分析需求，生成设计方案
2. **执行阶段** - Codex 实现代码，Claude 审查
3. **交付阶段** - 代码审查，提交

### 快速开发

```bash
/hybrid-lite-dev <任务描述>
```

适用于小任务（最多 3 个文件）。

## 权限配置

使用 Codex MCP 之前，需要在 Claude Code 配置中添加权限。在 `~/.claude/settings.json` 中添加：

```json
{
  "permissions": {
    "allow": [
      "mcp__codex-mcp-server__ping",
      "mcp__codex-mcp-server__ask-codex",
      "mcp__codex-mcp-server__batch-codex",
      "mcp__codex-mcp-server__version",
      "Bash(codex:*)",
      "Bash(gpt-5:*)",
      "Bash(o3:*)",
      "Bash(o4-mini:*)",
      "Bash(codex-mini-latest:*)"
    ]
  }
}
```

**注意**: 没有此配置，Codex MCP 调用会报 `sandbox policy` 错误。

### Codex CLI 配置

如果仍然报 sandbox 错误，需要修改 Codex CLI 配置 `~/.codex/config.toml`：

```toml
[windows]
sandbox = "disabled"

[projects.'你的项目路径']
trust_level = "trusted"
```

**配置说明：**
- `sandbox = "disabled"` - 禁用 Windows 沙盒限制
- `trust_level = "trusted"` - 将项目设置为信任级别

## Codex MCP 优化

本项目包含针对 Codex MCP (@cexll/codex-mcp-server v1.2.5) 的优化，解决 token 超限问题：

- **Prompt 模板**: 精简返回格式，减少 token 消耗
- **参数修复**: 使用 `fullAuto: true` 替代 `sandbox: true`
- **任务拆分**: 大任务拆分为小任务串行执行

### MCP 调用示例

```typescript
await mcp__codex-mcp-server__ask-codex({
  prompt: "【任务要求】\n1. 创建文件\n2. 完成后返回：SUCCESS | 文件路径 | 功能描述\n【任务内容】\n创建 Student.java",
  fullAuto: true,  // 重要：sandbox:true 不工作
  timeout: 60000
});
```

## 项目结构

```
hybrid-dev-workflow/
├── skills/
│   ├── hybrid-dev-workflow/   # 主工作流
│   ├── hybrid-execution/      # 执行阶段
│   ├── hybrid-planning/       # 规划阶段
│   └── hybrid-quick-dev/      # 快速开发
└── templates/                 # 模板文件
```

## 许可证

MIT

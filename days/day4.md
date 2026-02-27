# 第 4 章：编程智能体模式

## 课程概述

开发者正从"做"变为"管理"。Subagents 是未来趋势：agents 管理 agents。

### 学习目标
- 理解 Agent 管理的设计模式
- 掌握 Claude Code 的使用技巧
- 学习 Hooks、Commands、Subagents 的使用
- 了解 Anthropic 内部实践经验

---

## 1. Agent 管理技巧

### 软件任务步骤

```
1. 提供高级需求
2. 将需求转化为设计文档
3. 从文档实现解决方案
4. 添加测试
5. 确保 CI 通过
6. Code Review
7. 更新文档
```

### 四种技术

#### Hooks（钩子）
> 确定性的脚本，在预定义事件类型上运行

- `PreToolUse` - 工具使用前
- `PostToolUse` - 工具使用后
- `UserPromptSubmit` - 用户提交提示时
- `PreCompact` - 压缩前

#### Commands（命令）
> 将常用提示保存为文件供 Agent 执行

- 运行测试
- 代码审查
- Git 提交和推送

#### Subagents（子代理）
> 运行时委托，创建独立开发者角色

- 为不同类型工作创建不同开发者角色（前端、后端等）
- 清晰分离不同工作流的上下文
- 自定义系统提示、工具和独立上下文窗口
- 走向 agents 管理 agents

#### Agent Behavior Files
- `CLAUDE.md` / `cursorrules` / `AGENTS.md`

---

## 2. Claude Code 深度使用

### 安装
```bash
npm install -g @anthropic-ai/claude-code
```

### 核心使用场景

1. **Codebase Q&A + Research** - 查看代码结构、理解代码逻辑
2. **Write Code** - 1-shot（单次）、Sidekick（助手）、Prototype（原型）
3. **Integrate Tools & MCPs** - 集成外部工具
4. **Power Automation** - 自动化任务

### 工作流适配任务

| 任务类型 | 工作流 |
|----------|--------|
| 探索/计划 | explore → plan → confirm → code → commit |
| 测试驱动 | tests → commit → code → iterate → commit |
| 原型迭代 | code → screenshot → iterate |

### 关键教训

1. **Build for the model six months from now** - 为六个月后的模型构建
2. **Be ready to evolve** - 准备好演进
3. **Ask not what the model can do for you** - 不要问模型能为你做什么

---

## 3. Anthropic 内部实践案例

> 基于 **How Anthropic Teams Use Claude Code** 阅读材料

### 各团队 Claude Code 应用场景

| 团队 | 应用场景 |
|------|----------|
| **Data Infrastructure** | Kubernetes 调试、数据工作流自动化、新人代码库导航 |
| **Product Development** | 产品功能开发、Bug 修复、重构 |
| **Security Engineering** | 安全代码审查、漏洞修复 |
| **Data Science** | 数据分析、可视化 |
| **API Team** | API 文档生成、SDK 开发 |
| **Growth Marketing** | A/B 测试分析、营销自动化 |
| **Product Design** | 设计系统文档、原型迭代 |

### 最佳实践要点（来自 Anthropic 团队）

1. **详细的 Claude.md 文件** - 越详细的文档，Claude Code 表现越好
2. **使用 MCP 服务器** - 扩展 Claude Code 能力
3. **截图辅助** - 用截图展示期望的界面
4. **增量开发** - 一次实现一个步骤
5. **会话末文档** - 总结完成的工作，改进工作流

---

## 4. 实践练习

### 练习 1: 配置 CLAUDE.md
创建项目的 CLAUDE.md，包含：
- 项目简介
- 常用命令
- 代码风格
- 测试说明

### 练习 2: 使用 Claude Code
1. 安装 Claude Code
2. 探索代码库
3. 尝试编写代码

### 练习 3: 添加 MCP
尝试添加一个 MCP Server，如：
```bash
claude mcp add barley_server -- node myserver
```

---

## 讲座资料

### Lecture 7: How to be an Agent Manager
- [Slides (PDF)](../slides/week4-lecture1-agent-manager.pdf)
- **Guest Speaker**: Boris Cherny, Anthropic

### Lecture 8: Welcome to Claude Code
- [Slides (PDF)](../slides/week4-lecture2-claude-code.pdf)

---

## 阅读材料

### 必读
1. **[Claude Code 官方文档](https://docs.anthropic.com/en/docs/claude-code)**
2. **[How Anthropic Uses Claude Code (PDF)](../readings/how-anthropic-uses-claude-code.pdf)**

---

## 作业

**[Day 4 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week4)**

实践 Agent 管理技巧，创建自定义工作流。

---

## 明天预告

Day 5 将探讨现代终端工具，学习 AI 开发产品的设计原则。

---

*学习时间建议: 10-12 小时*

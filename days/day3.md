# Day 3: AI IDE and Context Management
# 第三天：AI 集成开发环境

## 课程概述

AI IDE 本质是增强而非替代。上下文质量决定输出质量。

### 学习目标
- 理解 AI IDE 的工作原理
- 掌握 AI IDE 的最佳实践
- 学习同步与异步工具的使用场景
- 理解 2025 年的编程工作流

---

## 1. AI IDE 两种模式

### 基础模式 (Bread-and-butter modes)
- **Inline** - 行内补全
- **Function** - 函数级
- **Single-file** - 单文件
- **Multi-file** - 多文件

### 原生 AI 模式 (True AI-native)
- **Background agents** - 后台代理
- **MCP 集成** - MCP 集成
- **Learn memories** - 学习记忆
- **Bugbot** - PR 审查

---

## 2. AI IDE 工作原理

### Tab Complete（标签补全）
1. 当前代码周围的小上下文窗口被加密
2. 服务器接收并进行 infilling LLM 推理
3. 建议返回并显示

### Chat（对话模式）
1. 代码块作为嵌入存储在服务器的语义索引中
2. 用户提问时检索相关代码
3. 将检索到的代码注入上下文
4. LLM 生成回答

### Context Management
- 代码分块存储为 embeddings
- 语义索引支持模糊搜索
- 文件名被混淆处理保护隐私

---

## 3. 同步 vs 异步工具

### 三个时代的 AI 编程工具

| 时代 | 工具 | 效率提升 |
|------|------|----------|
| 1 | GitHub Copilot | ~10% |
| 2 | AI IDEs (Cursor) | ~20% |
| 3 | AI Agents (Devin) | 6-12x |

### 同步 (Sync)
- 单线程、人在循环中
- AI agent 工作时间：20秒 - 1.5分钟
- 保持心流状态

### 异步 (Async)
- 多线程、人类委托
- AI agent 工作时间：10分钟 - 数小时
- 10x 并行能力

### 工具选择

| 阶段 | 推荐工具 |
|------|----------|
| 规划 | DeepWiki, Devin, Codemaps |
| 编码 | Windsurf（同步）, Devin（异步） |
| 测试 | Windsurf（同步测试和迭代） |

### 2025 编程工作流

```
Planning → Coding → Testing
   ↓           ↓          ↓
sync/async   sync       sync
```

---

## 4. 最佳实践

### 编写有效的任务描述

| 要素 | 描述 |
|------|------|
| **Goal** | 变更的目的是什么？ |
| **Definitions** | 什么特殊情况需要考虑？ |
| **Out-of-scope** | 什么*不应该*被改变？ |
| **Test cases** | 如何进行测试？ |
| **Plan** | 高级实现分解 |

### 优化代码库

> "Optimize your codebase so that a human and an agent could understand what's going on"

- **描述性**：Repo 方向、文件结构
- **可运行性**：设置和环境
- **一致性**：最佳实践、代码风格
- **可访问性**：访问模式、API 和契约

### 导航文件

| 文件 | 用途 |
|------|------|
| **CLAUDE.md** | Claude 自动加载的上下文文件 |
| **cursorrules** | Cursor 的规则配置 |
| **AGENTS.md** | 开放格式的 Agent 指令 |

---

## 5. 实践练习

### 练习 1: 配置 CLAUDE.md
创建一个 CLAUDE.md 文件，包含：
- 项目简介
- 常用命令
- 代码风格指南
- 测试说明

### 练习 2: 尝试同步/异步工具
1. 使用 Windsurf 进行同步编码
2. 使用 Devin 进行异步任务
3. 比较两者的使用体验

---

## 讲座资料

### Lecture 5: The AI IDE: Fundamentals to Power User
- [Slides (PDF)](../slides/week3-lecture1-ide-setup.pdf)
- **Guest Speaker**: Silas Alberti, Cognition

### Lecture 6: IDEs Love Agents
- [Slides (PDF)](../slides/week3-lecture2-cognition.pdf)

---

## 阅读材料

1. **[Claude Code 文档](https://docs.anthropic.com/en/docs/claude-code)**
2. **[Cursor 文档](https://cursor.sh/docs)**

---

## 作业

**[Day 3 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week3)**

熟悉 AI IDE 环境，掌握最佳实践。

---

## 明天预告

Day 4 将深入探讨 Agent 管理技巧，学习如何高效管理多个 AI 代理。

---

*学习时间建议: 10-12 小时*

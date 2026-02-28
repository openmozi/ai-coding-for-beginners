# 第 3 章：AI 集成开发环境

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

### Tab Complete（补全）
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

## 3. AI IDE 发展历史

| 年份 | 里程碑 |
|------|--------|
| 1980 | Turbo Pascal 发布，第一个真正的 IDE |
| 1983 | Microsoft Visual Studio 发布 |
| 1997 | IntelliJ IDEA 发布，先进的上下文代码导航、重构、代码补全 |
| 2001 | Microsoft VSCode 发布，轻量级编辑器，高度可扩展生态 |
| 2023 | Cursor 发布，首批广泛使用的 AI 原生 IDE |
| 2030 | 未来展望 |

---

## 4. 同步 vs 异步工具

### 三个时代的 AI 编程工具

| 时代 | 工具 | 效率提升 | 特点 |
|------|------|----------|------|
| 1 | GitHub Copilot | ~10% | 代码补全，本地开发 |
| 2 | AI IDEs (Cursor) | ~20% | 单任务完成，云端协作 |
| 3 | AI Agents (Devin) | 6-12x | 多任务并行，云端异步 |

### 同步 (Sync)
- **定义**: 单线程、人在循环中、注意力集中在一个任务上
- **AI agent 工作时间**: 20秒 - 1.5分钟
- **保持心流状态**
- **本地工具**: Windsurf

### 异步 (Async)
- **定义**: 多线程、人类委托、注意力在多个任务间切换
- **AI agent 工作时间**: 10分钟 - 数小时
- **10x 并行能力**
- **云端工具**: Devin, DeepWiki, Codemaps

### 半异步 (Semi-Async)
- **时间**: 3-10 分钟
- **问题**: 太慢保持心流，太快无法多任务
- **建议**: 避免或加快速度保持心流

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

## 5. 最佳实践

### 编写有效的任务描述

| 要素 | 描述 |
|------|------|
| **Goal** | 变更的目的是什么？ |
| **Definitions** | 什么特殊情况需要考虑？ |
| **Out-of-scope** | 什么*不应该*被改变？ |
| **Test cases** | 如何进行测试？ |
| **Plan** | 高级实现分解 |
| **Edge cases** | 代码库的相关部分及原因 |
| **Source files** | 需要更改的源文件 |
| **Prereqs** | LLM 需要知道的问题前提 |
| **Extensions** | 以后可能相关的更改 |

### 优化代码库

> "Optimize your codebase so that a human and an agent could understand what's going on"

- **描述性**: Repo 方向、文件结构
- **可运行性**: 设置和环境
- **一致性**: 最佳实践、代码风格
- **可访问性**: 访问模式、API 和契约

**提示**: 仓库中使用 monorepo 设计是高度推荐的

### 导航文件

| 文件 | 用途 |
|------|------|
| **CLAUDE.md** | Claude 自动加载的上下文文件 |
| **cursorrules** | Cursor 的规则配置 |
| **AGENTS.md** | 开放格式的 Agent 指令 |
| **llms.txt** | 为LLM抓取网页提供导航指导 |

**注意**: Agent 并不总是遵守这些描述/指令，它们仅供参考。

---

## 6. 实践练习

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

### 练习 3: 探索 AI IDE 功能
1. 尝试 Tab Complete
2. 尝试 Chat 模式
3. 探索 MCP 集成

---

## 讲座资料

### Lecture 5: The AI IDE: Fundamentals to Power User
- [Slides (PDF)](../slides/week3-lecture1-ide-setup.pdf)
- **Guest Speaker**: Silas Alberti, Cognition（Head of Research）
- **日期**: 10/10/25, 8:30am PT, 420-041

### Lecture 6: IDEs Love Agents
- [Slides (PDF)](../slides/week3-lecture2-cognition.pdf)
- **核心内容**: 同步 vs 异步工具，2025 编程工作流

---

## 阅读材料

1. **[Claude Code 文档](https://docs.anthropic.com/en/docs/claude-code)**
2. **[Cursor 文档](https://cursor.sh/docs)**

---

## 作业

**[Chapter 3 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week3)**

熟悉 AI IDE 环境，掌握最佳实践。

---

## 下一章

[下一章：Chapter 4](./chapter4.md)

---

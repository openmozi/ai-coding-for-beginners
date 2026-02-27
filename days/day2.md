# Day 2: The Anatomy of Coding Agents
# 第二天：编程智能体的架构

## 课程概述

Agent 是 AI 编程的核心能力。理解底层原理才能更好使用工具。

### 学习目标
- 理解 Agent 架构的核心组件
- 掌握工具使用和函数调用机制
- 学习 MCP (Model Context Protocol) 协议
- 从零构建一个简单的 Coding Agent

---

## 1. 什么是 Coding Agent？

```
Agent = LLM + 工具 + 循环
```

- **LLM** 负责推理和决策
- **工具** 让 Agent 与世界交互
- **循环** 让 Agent 持续工作直到完成任务

### Agent 架构核心步骤

```
1. 读取用户输入 → 追加到对话
2. 告诉 LLM 可用工具（Read_file, List_dir, Edit_file, Create_file）
3. LLM 在适当时候请求使用工具
4. 本地执行工具并返回结果
5. 对话继续直到任务完成
```

### Claude 的秘诀

1. **Front-load context** - 用小而精准的提示预先加载上下文
2. **System-reminder 标签** - 处处使用 <system-reminder> 防止行为漂移
3. **命令前缀提取** - 清晰提取用户命令
4. **子代理（Subagents）** - 生成子代理帮助防止上下文过载

---

## 2. 工具使用与 Function Calling

### Function Calling 原理

```json
{
  "name": "get_weather",
  "description": "获取指定城市的天气信息",
  "parameters": {
    "type": "object",
    "properties": {
      "city": { "type": "string", "description": "城市名称" }
    },
    "required": ["city"]
  }
}
```

### 工作流程

1. 定义工具的名称、描述和参数模式
2. LLM 根据用户请求决定何时调用工具
3. 执行工具并返回结果给 LLM
4. LLM 继续生成响应或请求更多工具

---

## 3. MCP (Model Context Protocol)

### 为什么需要 MCP？

- LLM 拥有大量但静态的世界知识，只有在重新训练时才会更新
- 构建完全自主的系统需要稳健的方式来输入动态数据

### MCP 定义

> Model Context Protocol：一个允许系统以通用方式向 AI 模型提供上下文的协议

### MCP 优势

| 优势 | 描述 |
|------|------|
| **标准化** | 统一的工具描述格式 |
| **可扩展** | MCP Server 可以包装任何工具 |
| **减少集成工作** | M x N → M + N |

### MCP 架构

| 组件 | 描述 |
|------|------|
| **Host** | Cursor, Claude Desktop 等 AI IDE |
| **MCP Client** | 嵌入在 Host 中的库 |
| **MCP Server** | 工具前端的轻量级包装器 |
| **Tool** | 可调用的函数 |

### MCP 通信流程

```
1. Client 调用 tools/list 获取服务器能力
2. Server 返回 JSON 描述每个工具
3. Host 将工具描述注入模型上下文
4. 用户提示触发模型，发送结构化工具调用
5. MCP Server 执行工具，对话继续
```

### MCP 局限性

- Agent 对大量工具处理不佳
- API 快速消耗上下文窗口
- 设计 API 时要考虑 AI 的使用方式

---

## 4. 实践练习

### 练习 1: 理解 Agent 循环
在 Claude 或 Cursor 中观察 Agent 如何：
1. 接收用户请求
2. 决定使用哪些工具
3. 执行工具并处理结果
4. 继续直到任务完成

### 练习 2: 探索 MCP
1. 在 Cursor 或 Claude Desktop 中查看可用的 MCP
2. 尝试添加一个新的 MCP Server
3. 观察工具如何被描述给 LLM

---

## 讲座资料

### Lecture 3: Building a coding agent from scratch
- [Slides (PDF)](slides/week2-lecture1-coding-agent-scratch.pdf)

### Lecture 4: Building a custom MCP server
- [Slides (PDF)](slides/week2-lecture2-mcp-server.pdf)

---

## 阅读材料

1. **[MCP Introduction](https://stytch.com/blog/model-context-protocol-introduction/)**
2. **[Sample MCP Server Implementations](https://github.com/modelcontextprotocol/servers)**

---

## 作业

**[Day 2 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week2)**

在 AI IDE 中完成开发任务。

---

## 明天预告

Day 3 将深入探讨 AI IDE，学习上下文管理和代码理解的最佳实践。

---

*学习时间建议: 10-12 小时*

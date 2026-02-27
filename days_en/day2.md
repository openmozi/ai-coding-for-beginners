# Chapter 2: The Anatomy of Coding Agents

## Course Overview

Agent is the core capability of AI programming. Understanding underlying principles helps use tools better.

### Learning Objectives
- Understand Agent architecture core components
- Master tool use and function calling
- Learn MCP (Model Context Protocol)
- Build a simple Coding Agent from scratch

---

## 1. What is a Coding Agent?

```
Agent = LLM + Tools + Loop
```

- **LLM** handles reasoning and decision making
- **Tools** enable Agent to interact with the world
- **Loop** allows Agent to continue working until task completion

### Agent Architecture Steps

```
1. Read user input → append to conversation
2. Tell LLM available tools (Read_file, List_dir, Edit_file, Create_file)
3. LLM requests tool use at appropriate time
4. Execute tool locally and return results
5. Continue until task is complete
```

### Claude's Secrets

1. **Front-load context** - Use small, targeted prompts
2. **System-reminder tags** - Prevent behavior drift
3. **Command prefix extraction** - Clearly extract commands
4. **Subagents** - Prevent context overload

---

## 2. Tool Use and Function Calling

### Function Calling Principle

```json
{
  "name": "get_weather",
  "description": "Get weather information",
  "parameters": {
    "type": "object",
    "properties": { "city": { "type": "string" } },
    "required": ["city"]
  }
}
```

### Workflow

1. Define tool name, description, parameter schema
2. LLM decides when to call tools
3. Execute tool and return results
4. LLM continues or requests more tools

---

## 3. MCP (Model Context Protocol)

### Why MCP?
- LLMs have vast but static world knowledge
- Building autonomous systems needs robust dynamic data input

### MCP Definition

> Model Context Protocol: A protocol that allows systems to provide context to AI models in a generalizable way

### MCP Benefits

| Benefit | Description |
|---------|-------------|
| **Standardization** | Unified tool description format |
| **Extensibility** | MCP Server can wrap any tool |
| **Reduced Integration** | M x N → M + N |

### MCP Architecture

| Component | Description |
|-----------|-------------|
| **Host** | Cursor, Claude Desktop, etc. |
| **MCP Client** | Library embedded in Host |
| **MCP Server** | Lightweight wrapper for tools |
| **Tool** | Callable function |

### MCP Limitations

- Agents don't handle many tools well
- APIs consume context quickly
- Design APIs with AI in mind

---

## 4. Practice Exercises

### Exercise 1: Understand Agent Loop
Observe in Claude or Cursor how Agent:
1. Receives user request
2. Decides which tools to use
3. Executes tools and processes results
4. Continues until task completion

### Exercise 2: Explore MCP
1. View available MCPs in Cursor or Claude Desktop
2. Try adding a new MCP Server
3. Observe how tools are described to LLM

---

## Lecture Materials

### Lecture 3: Building a coding agent from scratch
- [Slides (PDF)](../slides/week2-lecture1-coding-agent-scratch.pdf)

### Lecture 4: Building a custom MCP server
- [Slides (PDF)](../slides/week2-lecture2-mcp-server.pdf)

---

## Reading Materials

1. **[MCP Introduction](https://stytch.com/blog/model-context-protocol-introduction/)**
2. **[Sample MCP Server Implementations](https://github.com/modelcontextprotocol/servers)**

---

## Assignment

**[Day 2 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week2)**

---

## Tomorrow's Preview

Day 3 will explore AI IDE, learning context management and code understanding best practices.

---

*Learning Time: 10-12 hours*

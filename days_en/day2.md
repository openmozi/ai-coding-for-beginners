# Chapter 2: Coding Agent Architecture

## Course Overview

Agents are the core capability of AI programming. Understanding the underlying principles helps you use tools better.

### Learning Objectives
- Understand core components of Agent architecture
- Master tool use and function calling mechanisms
- Learn MCP (Model Context Protocol)
- Build a simple Coding Agent from scratch

---

## 1. What is a Coding Agent?

```
Agent = LLM + Tools + Loop
```

- **LLM** is responsible for reasoning and decision-making
- **Tools** allow agents to interact with the world
- **Loop** enables the agent to continue working until the task is complete

### Agent Architecture Core Steps

```
1. Read user input → append to conversation
2. Tell LLM available tools (Read_file, List_dir, Edit_file, Create_file)
3. LLM requests tool use at appropriate time
4. Execute tool locally and return result
5. Continue conversation until task is complete
```

### Terminology

| Term | Description |
|------|-------------|
| **System Prompt** | Defines overall LLM behavior and some directives |
| **User Prompt** | User's custom requests |
| **Assistant Prompt** | LLM's response |

### Claude's Secret Sauce

1. **Front-load context** - Use tiny targeted prompts to preload context
2. **System-reminder tags** - Use <system-reminder> everywhere to prevent drift
3. **Command prefix extraction** - Clearly extract user commands
4. **Subagents** - Spawn subagents to help prevent context overloading

---

## 2. Tool Use and Function Calling

### Function Calling Principle

```json
{
  "name": "get_weather",
  "description": "Get weather information for specified city",
  "parameters": {
    "type": "object",
    "properties": {
      "city": { "type": "string", "description": "City name" }
    },
    "required": ["city"]
  }
}
```

### Common Tools
- **Read_file** - Read file content
- **List_dir** - List directory contents
- **Edit_file** - Edit files
- **Create_file** - Create new files

### Workflow

1. Define tool name, description, and parameter schema
2. LLM decides when to call tools based on user request
3. Execute tool and return result to LLM
4. LLM continues generating responses or requesting more tools

---

## 3. MCP (Model Context Protocol)

### Why MCP?

- LLMs have vast but static world knowledge that only updates when retrained
- Building fully autonomous systems requires robust ways to feed dynamic data

**Dynamic Data Examples**:
- What's the weather today?
- Who is the president?
- What's the price of Bitcoin?
- Who is the narrator in Nike's latest ad campaign?

RAG and tool-calling are the best answers we have today.

### MCP Definition

> Model Context Protocol: A protocol that allows systems to provide context to AI models in a generalizable way

### MCP Benefits

| Benefit | Description |
|---------|-------------|
| **Standardization** | Unified tool description format using JSON-RPC |
| **Extensibility** | MCP Server can wrap any tool |
| **Reduced Integration** | M x N → M + N |
| **Inherited from LSP** | Extends from Language Server Protocols |
| **Proactive Workflows** | Supports proactive agentic workflows, not just reactive responses |

### MCP Architecture

| Component | Description |
|-----------|-------------|
| **Host** | AI IDEs like Cursor, Claude Desktop |
| **MCP Client** | Library embedded in Host (stateful session per server) |
| **MCP Server** | Lightweight wrapper in front of a tool |
| **Tool** | Callable function (could be data source, API) |

### MCP Communication Flow

```
1. Client calls tools/list to get server capabilities
2. Server returns JSON describing each tool (name, summary, JSON schema)
3. Host injects tool description into model context
4. User prompt triggers model, emitting structured tool call
5. MCP Server executes tool, conversation resumes

MCP provides stdio and SSE transport layer
```

### MCP Limitations

- **Limited tool handling**: Agents don't handle many tools well
- **Context window consumption**: APIs eat up context window quickly
- **AI-native design**: Design APIs with AI usage in mind

---

## 4. Practice Exercises

### Exercise 1: Understand Agent Loop
Observe how Agent in Claude or Cursor:
1. Receives user requests
2. Decides which tools to use
3. Executes tools and processes results
4. Continues until task is complete

### Exercise 2: Explore MCP
1. View available MCPs in Cursor or Claude Desktop
2. Try adding a new MCP Server
3. Observe how tools are described to LLM

### Exercise 3: Build Simple Agent
Try building a simple Coding Agent from scratch:
1. Set up LLM API
2. Define available tools
3. Implement agent loop
4. Test basic functionality

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

Complete development tasks in AI IDE.

---

## Tomorrow's Preview

Day 3 will dive into AI IDE, learning context management and code understanding best practices.

---


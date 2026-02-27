# Day 3: AI IDE and Context Management

## Course Overview

AI IDE is enhancement, not replacement. Context quality determines output quality.

### Learning Objectives
- Understand how AI IDE works
- Master AI IDE best practices
- Learn sync vs async tool use cases
- Understand 2025 programming workflow

---

## 1. AI IDE Two Modes

### Basic Modes
- **Inline** - inline completion
- **Function** - function-level
- **Single-file**
- **Multi-file**

### AI-native Modes
- **Background agents**
- **MCP integration**
- **Learn memories**
- **Bugbot** - PR review

---

## 2. How AI IDE Works

### Tab Complete
1. Small context window around current code encrypted
2. Server runs infilling LLM inference
3. Suggestion returned

### Chat Mode
1. Code stored as embeddings in semantic index
2. Retrieve relevant code when user asks
3. Inject into context
4. LLM generates answer

---

## 3. Sync vs Async Tools

### Three Eras of AI Coding Tools

| Era | Tool | Efficiency Gain |
|-----|------|-----------------|
| 1 | GitHub Copilot | ~10% |
| 2 | AI IDEs (Cursor) | ~20% |
| 3 | AI Agents (Devin) | 6-12x |

### Sync
- Single-threaded, human in loop
- 20 seconds - 1.5 minutes
- Maintains flow state

### Async
- Multi-threaded, human delegates
- 10 minutes - hours
- 10x parallelism

### Tool Selection

| Stage | Recommended Tools |
|-------|-------------------|
| Planning | DeepWiki, Devin, Codemaps |
| Coding | Windsurf (sync), Devin (async) |
| Testing | Windsurf (sync) |

### 2025 Workflow

```
Planning → Coding → Testing
   ↓           ↓          ↓
sync/async   sync       sync
```

---

## 4. Best Practices

### Writing Effective Task Descriptions

| Element | Description |
|---------|-------------|
| **Goal** | What is the purpose of change? |
| **Definitions** | Special cases to consider? |
| **Out-of-scope** | What should NOT be changed? |
| **Test cases** | How to test? |

### Navigation Files

| File | Purpose |
|------|---------|
| **CLAUDE.md** | Claude auto-loads context |
| **cursorrules** | Cursor's rule config |
| **AGENTS.md** | Open format for Agent instructions |

---

## Lecture Materials

### Lecture 5: The AI IDE: Fundamentals to Power User
- [Slides (PDF)](slides/week3-lecture1-ide-setup.pdf)
- **Guest Speaker**: Silas Alberti, Cognition

### Lecture 6: IDEs Love Agents
- [Slides (PDF)](slides/week3-lecture2-cognition.pdf)

---

## Reading Materials

1. **[Claude Code Docs](https://docs.anthropic.com/en/docs/claude-code)**
2. **[Cursor Docs](https://cursor.sh/docs)**

---

## Assignment

**[Day 3 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week3)**

---

## Tomorrow's Preview

Day 4 will explore Agent management techniques, learning how to efficiently manage multiple AI agents.

---

*Learning Time: 10-12 hours*

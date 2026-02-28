# Chapter 3: AI Integrated Development Environment

## Course Overview

AI IDE is fundamentally about augmentation, not replacement. Context quality determines output quality.

### Learning Objectives
- Understand how AI IDE works
- Master AI IDE best practices
- Learn sync vs async tool usage scenarios
- Understand 2025 programming workflows

---

## 1. Two Modes of AI IDE

### Bread-and-butter Modes
- **Inline** - Inline completion
- **Function** - Function-level
- **Single-file** - Single file
- **Multi-file** - Multi-file

### True AI-native Modes
- **Background agents** - Background agents
- **MCP integration** - MCP integration
- **Learn memories** - Learning memories
- **Bugbot** - PR review

---

## 2. How AI IDE Works

### Tab Complete
1. Small context window around current code is encrypted
2. Server receives and runs infilling LLM inference
3. Suggestion sent back and displayed

### Chat Mode
1. Code chunks stored as embeddings in semantic index on server
2. When user asks, retrieve relevant code
3. Inject retrieved code into context
4. LLM generates answer

### Context Management
- Code chunks stored as embeddings
- Semantic index supports fuzzy search
- Filenames obfuscated for privacy

---

## 3. AI IDE History

| Year | Milestone |
|------|-----------|
| 1980 | Turbo Pascal released, first true IDE |
| 1997 | Microsoft Visual Studio released |
| 2001 | IntelliJ IDEA released with advanced contextual code navigation, refactoring, code completion |
| 2015 | VSCode released - lightweight editor with highly extensible ecosystem |
| 2023 | Cursor released, one of first widely used AI native IDEs |
| 2030 | Future outlook |

---

## 4. Sync vs Async Tools

### Three Eras of AI Coding Tools

| Era | Tool | Efficiency Gain | Characteristics |
|-----|------|-----------------|-----------------|
| 1 | GitHub Copilot | ~10% | Code completion, local development |
| 2 | AI IDEs (Cursor) | ~20% | Single task completion, cloud collaboration |
| 3 | AI Agents (Devin) | 6-12x | Multi-task parallel, cloud async |

### Synchronous (Sync)
- **Definition**: Single-threaded, human-in-the-loop, attention focused on one task
- **AI agent work time**: 20 seconds - 1.5 minutes
- **Maintain flow state**
- **Local tools**: Windsurf

### Asynchronous (Async)
- **Definition**: Multi-threaded, human delegates to AI, switches attention between multiple tasks
- **AI agent work time**: 10 minutes - multiple hours
- **10x parallelism**
- **Cloud tools**: Devin, DeepWiki, Codemaps

### Semi-Async
- **Time**: 3-10 minutes
- **Problem**: Too slow for flow, too fast for multi-tasking
- **Suggestion**: Avoid or make faster to preserve flow

### Tool Selection

| Phase | Recommended Tools |
|-------|-------------------|
| Planning | DeepWiki, Devin, Codemaps |
| Coding | Windsurf (sync), Devin (async) |
| Testing | Windsurf (sync testing and iteration) |

### 2025 Programming Workflow

```
Planning → Coding → Testing
   ↓           ↓          ↓
sync/async   sync       sync
```

---

## 5. Best Practices

### Writing Effective Task Descriptions

| Element | Description |
|---------|-------------|
| **Goal** | What is the purpose of the change? |
| **Definitions** | What special cases need to be accounted for? |
| **Out-of-scope** | What should *not* be changed? |
| **Test cases** | How will testing be done? |
| **Plan** | High-level implementation breakdown |
| **Edge cases** | What parts of the codebase are relevant and why? |
| **Source files** | Source files being changed |
| **Prereqs** | What prereqs does the LLM need to know about the problem? |
| **Extensions** | What changes will be relevant later so the LLM can future-proof its design? |

### Optimizing Your Codebase

> "Optimize your codebase so that a human and an agent could understand what's going on"

- **Descriptive**: Repo orientation, file structure
- **Runnable**: Setup and environment
- **Consistent**: Best practices, code style
- **Accessible**: Access patterns, APIs and contracts

**Tip**: A monorepo design in your repo is highly encouraged

### Navigation Files

| File | Purpose |
|------|---------|
| **CLAUDE.md** | Context file auto-loaded by Claude |
| **cursorrules** | Cursor's rule configuration |
| **AGENTS.md** | Open format for Agent instructions |
| **llms.txt** | Provide navigation guidance for LLMs scraping the web |

**Note**: Agents won't always adhere to these descriptions/directives. They are intended as guidance.

---

## 6. Practice Exercises

### Exercise 1: Configure CLAUDE.md
Create a CLAUDE.md file containing:
- Project introduction
- Common commands
- Code style guidelines
- Testing instructions

### Exercise 2: Try Sync/Async Tools
1. Use Windsurf for sync coding
2. Use Devin for async tasks
3. Compare user experience

### Exercise 3: Explore AI IDE Features
1. Try Tab Complete
2. Try Chat mode
3. Explore MCP integration

---

## Lecture Materials

### Lecture 5: The AI IDE: Fundamentals to Power User
- [Slides (PDF)](../slides/week3-lecture1-ide-setup.pdf)
- **Guest Speaker**: Silas Alberti, Cognition (Head of Research)
- **Date**: 10/10/25, 8:30am PT, 420-041

### Lecture 6: IDEs Love Agents
- [Slides (PDF)](../slides/week3-lecture2-cognition.pdf)
- **Core**: Sync vs async tools, 2025 programming workflow

---

## Reading Materials

1. **[Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)**
2. **[Cursor Documentation](https://cursor.sh/docs)**

---

## Assignment

**[Chapter 3 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week3)**

Familiarize with AI IDE environment and master best practices.

---

## Next Chapter

[Next Chapter: Chapter 4](./chapter4.md)

---

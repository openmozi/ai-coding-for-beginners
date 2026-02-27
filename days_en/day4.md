# Chapter 4: Agent Management and Claude Code

## Course Overview

Developers are transitioning from "doing" to "managing". Subagents are the future: agents managing agents.

### Learning Objectives
- Understand Agent management design patterns
- Master Claude Code usage
- Learn Hooks, Commands, Subagents
- Learn Anthropic internal practices

---

## 1. Agent Management Techniques

### Software Task Steps

```
1. Provide high level requirements
2. Convert to design doc
3. Implement solution
4. Add tests
5. Ensure CI passes
6. Code review
7. Update docs
```

### Four Techniques

#### Hooks
> Deterministic scripts on predefined event types

- PreToolUse
- PostToolUse
- UserPromptSubmit
- PreCompact

#### Commands
> Save frequently-used prompts as files

- Running tests
- Code review
- Git commit/push

#### Subagents
> Runtime delegation, independent personas

- Different developer roles
- Separate contexts
- Custom prompts and tools

#### Agent Behavior Files
- CLAUDE.md / cursorrules / AGENTS.md

---

## 2. Claude Code Deep Dive

### Installation
```bash
npm install -g @anthropic-ai/claude-code
```

### Core Use Cases

1. **Codebase Q&A + Research**
2. **Write Code** (1-shot, Sidekick, Prototype)
3. **Integrate Tools & MCPs**
4. **Power Automation**

### Key Lessons

1. Build for the model six months from now
2. Be ready to evolve
3. Ask not what model can do for you

---

## 3. Anthropic Internal Practice Cases

> Based on **How Anthropic Teams Use Claude Code**

### Team Use Cases

| Team | Use Cases |
|------|-----------|
| **Data Infrastructure** | Kubernetes debugging, data workflow automation |
| **Product Development** | Feature development, bug fixes |
| **Security Engineering** | Security code review |
| **Data Science** | Data analysis, visualization |
| **API Team** | API documentation, SDK development |

### Best Practices (from Anthropic teams)

1. **Detailed Claude.md files** - Better documentation = better performance
2. **Use MCP servers** - Extend capabilities
3. **Screenshot assistance** - Show expected interfaces
4. **Incremental development** - One step at a time
5. **End-of-session documentation** - Summarize completed work

---

## Lecture Materials

### Lecture 7: How to be an Agent Manager
- [Slides (PDF)](../slides/week4-lecture1-agent-manager.pdf)
- **Guest Speaker**: Boris Cherny, Anthropic

### Lecture 8: Welcome to Claude Code
- [Slides (PDF)](../slides/week4-lecture2-claude-code.pdf)

---

## Reading Materials

1. **[Claude Code Official Docs](https://docs.anthropic.com/en/docs/claude-code)**
2. **[How Anthropic Uses Claude Code](../readings/how-anthropic-uses-claude-code.pdf)**

---

## Assignment

**[Day 4 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week4)**

---

## Tomorrow's Preview

Day 5 will explore modern terminal tools, learning AI developer product design principles.

---

*Learning Time: 10-12 hours*

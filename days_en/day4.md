# Chapter 4: Programming Agent Patterns

## Course Overview

Developers are transitioning from "doing" to "managing". Subagents are the future trend: agents managing agents.

### Learning Objectives
- Understand Agent management design patterns
- Master Claude Code usage
- Learn Hooks, Commands, Subagents usage
- Understand Anthropic internal practices

---

## 1. Development Evolution Trend

### Development Evolution Stages

| Stage | Description |
|-------|-------------|
| 1 | Single developer managing single developer's output |
| 2 | Lead managing many developers' output |
| 3 | Lead managing many developers' output (assisted by AI system) |
| 4 | Single developer managing many AI agents' work |

### Software Teams History

| Year | Milestone |
|------|-----------|
| 1940 | Solo developers handling full projects |
| 1960 | Software teams emerge driven by NASA, DoD projects |
| 1970 | Mainstream adoption of software teams, specialization emerges |
| 1990 | Teams with developers assisted by AI coding systems |
| 2023 | Teams with developers managing groups of diverse agents |
| 2025 | Software teams with developers assisted by AI coding systems |
| 2030 | Future outlook |

---

## 2. Software Task Steps

```
1. Provide high level requirements 🟩
2. Convert requirements into a design doc 🟩/🟦
3. Implement solution from doc 🟦
4. Add tests 🟦
5. Ensure CI passes 🟦
6. Code review 🟦
7. Update docs 🟦
```

---

## 3. Agent Management Techniques

### Four Techniques

#### Hooks
> Deterministic scripts that run on predefined event types

- `PreToolUse` - Before tool use
- `PostToolUse` - After tool use
- `UserPromptSubmit` - When user submits prompt
- `PreCompact` - Before compaction

#### Commands
> Provide frequently-used prompts as files that the agent can execute

- Running tests
- Code review
- Git commit and push

#### Subagents
> Runtime delegation, creating independent developer personas

**Purposes**:
- Create distinct developer personas for different types of work (frontend, backend, etc.)
- Cleanly separate contexts for different work streams
- Customized system prompts, tools, and separate context window
- A move toward agents managing other agents

**References**:
- https://github.com/vijaythecoder/awesome-claude-agents
- https://github.com/SuperClaude-Org/SuperClaude_Framework

#### Agent Behavior Files
- `CLAUDE.md` / `cursorrules` / `AGENTS.md`

### Best Practices

1. **You need careful backstops**
2. **Auditability of each agent**
   - Tests in codebase
   - CI/CD best practices
   - Label every diff made by an agent
3. **Different models for different classes of tasks**
   - More complex tasks may need more upfront handholding
   - Fully async ones may need less
4. **Checkpoint regularly (commit)**

---

## 4. Claude Code Deep Dive

### Installation
```bash
npm install -g @anthropic-ai/claude-code
```

### Core Use Cases

1. **Codebase Q&A + Research** - View code structure, understand code logic
```
> how do I make a new @app/services/ValidationTemplateFactory?
> why does recoverFromException take so many arguments? look through git history to answer
> why did we fix issue #18363 by adding the if/else in @src/login.ts api?
> in which version did we release the new @api/ext/PreHooks.php api?
> look at PR #9383, then carefully verify which app versions were impacted
> what did I ship last week?
```

2. **Write Code** - 1-shot, Sidekick, Prototype
3. **Integrate Tools & MCPs** - Integrate external tools
```bash
$ claude mcp add barley_server -- node myserver
```
4. **Power Automation** - Automate tasks

### Workflow Adaptation

| Task Type | Workflow |
|-----------|----------|
| Explore/Plan | explore → plan → confirm → code → commit |
| Test-driven | tests → commit → code → iterate → commit |
| Prototype iteration | code → screenshot → iterate → code... |

---

## 5. Anthropic Internal Practices

> Based on **How Anthropic Uses Claude Code** reading material

### Team Use Cases

| Team | Use Cases |
|------|-----------|
| **Data Infrastructure** | Kubernetes debugging, data workflow automation, onboarding code navigation |
| **Product Development** | Product feature development, bug fixes, refactoring |
| **Security Engineering** | Security code review, vulnerability fixes |
| **Data Science** | Data analysis, visualization |
| **API Team** | API documentation generation, SDK development |
| **Growth Marketing** | A/B test analysis, marketing automation |
| **Product Design** | Design system documentation, prototype iteration |

### Best Practices (from Anthropic teams)

1. **Detailed CLAUDE.md files** - More detailed documentation = better Claude Code performance
2. **Use MCP servers** - Extend Claude Code capabilities
3. **Screenshot assistance** - Use screenshots to show expected interface
4. **Incremental development** - Implement one step at a time
5. **End-of-session documentation** - Summarize completed work, improve workflows

### Claude Code SDK

```bash
# Using SDK
$ claude -p   "what did i do this week?"   --allowedTools Bash(git log:*)   --output-format stream-json

# Pipeline usage
$ get-gcp-logs 1uhd832d |
  claude -p "correlate errors + commits"   --output-format=json |
  jq '.result'
```

---

## 6. Key Lessons

1. **Build for the model six months from now**
2. **Be ready to evolve**
3. **Ask not what the model can do for you, ask what you can do for the model**
4. Programming language productivity is increasing exponentially (AI-driven)
5. IDE productivity is following similar exponential growth

---

## 7. Practice Exercises

### Exercise 1: Configure CLAUDE.md
Create project CLAUDE.md containing:
- Project introduction
- Common commands
- Code style
- Testing instructions

### Exercise 2: Use Claude Code
1. Install Claude Code
2. Explore codebase
3. Try writing code

### Exercise 3: Add MCP
Try adding an MCP Server:
```bash
claude mcp add barley_server -- node myserver
```

---

## Lecture Materials

### Lecture 7: How to be an Agent Manager
- [Slides (PDF)](../slides/week4-lecture1-agent-manager.pdf)
- **Guest Speaker**: Boris Cherny, Anthropic (Creator of Claude Code)
- **Date**: 10/17/25

### Lecture 8: Welcome to Claude Code
- [Slides (PDF)](../slides/week4-lecture2-claude-code.pdf)
- **Core**: Claude Code architecture, use cases, best practices

---

## Reading Materials

### Required
1. **[Claude Code Official Documentation](https://docs.anthropic.com/en/docs/claude-code)**
2. **[How Anthropic Uses Claude Code (PDF)](../readings/how-anthropic-uses-claude-code.pdf)**

---

## Assignment

**[Day 4 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week4)**

Practice Agent management techniques and create custom workflows.

---

## Tomorrow's Preview

Day 5 will discuss modern terminal tools and learn AI developer product design principles.

---


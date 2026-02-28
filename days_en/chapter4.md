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

### 1.1 Evolution of Developer Roles

```mermaid
graph LR
    subgraph "Four Stages of Development Evolution"
        S1[Stage 1<br/>Single Developer<br/>Managing Own Output]
        S2[Stage 2<br/>Team Lead<br/>Managing Developers]
        S3[Stage 3<br/>Team Lead + AI<br/>Managing Developer Output]
        S4[Stage 4<br/>Single Developer<br/>Managing Multiple AI Agents]
    end

    S1 --> S2 --> S3 --> S4

    style S1 fill:#bfb
    style S2 fill:#bbf
    style S3 fill:#f9f
    style S4 fill:#f55
```

| Stage | Role | Description |
|-------|------|-------------|
| 1 | Solo Developer | Single developer managing single developer's output |
| 2 | Team Lead | Lead managing many developers' output |
| 3 | AI-Assisted Team | Lead managing many developers' output (assisted by AI system) |
| 4 | Agent Manager | Single developer managing many AI agents' work |

### 1.2 History of Software Teams

```mermaid
timeline
    title Software Team Development History
    1940 : Solo developers handling full projects
    1960 : First software teams emerge<br/>(driven by NASA, DoD projects)
    1970 : Mainstream adoption of software teams<br/>Specialization emerges
    1990 : Software engineering matures<br/>Methodology and tool standardization
    2023 : Developers managing diverse agent groups
    2025 : Developers + AI coding systems collaboration
    2030 : Future outlook
```

| Year | Milestone | Key Change |
|------|-----------|------------|
| 1940 | Solo Developers | Single person handles full project |
| 1960 | First Teams | NASA, DoD project requirements |
| 1970 | Mainstream Adoption | Specialization emerges |
| 1990 | Engineering Maturity | Methodology and tool standardization |
| 2023 | Agent Group Management | Developers managing diverse agents |
| 2025 | AI Collaboration | Developers + AI coding systems |
| 2030 | Future Outlook | Agents managing agents |

---

## 2. Exponential Growth in Programming Productivity

### 2.1 Programming Language Productivity Evolution

```mermaid
graph LR
    subgraph "Programming Language Productivity Growth"
        direction LR
        A[1950s<br/>Fortran/Assembly] --> B[1960s<br/>Cobol/Basic]
        B --> C[1970s<br/>C/Pascal]
        C --> D[1980s<br/>C++/Objective-C]
        D --> E[1990s<br/>Java/Python]
        E --> F[2000s<br/>C#/Ruby]
        F --> G[2010s<br/>Go/Swift/Rust/TypeScript]
        G --> H[2020s<br/>AI-Assisted Coding]
    end
```

**Key Insight**: Programming language productivity is increasing exponentially, driven by AI.

### 2.2 IDE Productivity Evolution

```mermaid
graph LR
    subgraph "IDE Productivity Growth"
        I1[IBM 029<br/>1964] --> I2[ed<br/>1969]
        I2 --> I3[Smalltalk-80<br/>1980]
        I3 --> I4[Visual Basic<br/>1991]
        I4 --> I5[Eclipse<br/>2001]
        I5 --> I6[Sublime/Neovim<br/>2010s]
        I6 --> I7[Copilot<br/>2021]
        I7 --> I8[Devin/Claude Code<br/>2024]
    end
```

**Key Insight**: IDE productivity is following similar exponential growth, also driven by AI.

### 2.3 Verification Methods Evolution

```mermaid
graph TB
    subgraph "Verification Methods Evolution"
        V1[Manual Debugging]
        V2[Static Types<br/>Algol]
        V3[Automated Testing]
        V4[Continuous Integration<br/>CI]
        V5[Property Testing<br/>QuickCheck]
        V6[E2E Testing]
        V7[Chaos Testing<br/>Chaos Monkey]
        V8[AI-Powered Vulnerability Testing]
        V9[AI-Powered Unit Testing<br/>TestGen]
        V10[AI-Powered Fuzz Testing<br/>Sapienz]
        V11[Self Play]
    end

    V1 --> V2 --> V3 --> V4 --> V5 --> V6 --> V7 --> V8 --> V9 --> V10 --> V11

    style V8 fill:#f9f
    style V9 fill:#f9f
    style V10 fill:#f9f
    style V11 fill:#f9f
```

---

## 3. Software Task Steps and Responsibility Distribution

### 3.1 Task Steps Overview

```mermaid
graph TB
    subgraph "Software Task Steps"
        R1[Provide high level requirements 🟩]
        R2[Convert requirements into design doc 🟩/🟦]
        R3[Implement solution from doc 🟦]
        R4[Add tests 🟦]
        R5[Ensure CI passes 🟦]
        R6[Code review 🟦]
        R7[Update docs 🟦]
    end

    R1 --> R2 --> R3 --> R4 --> R5 --> R6 --> R7

    style R1 fill:#bfb
    style R2 fill:#ff9
    style R3 fill:#bbf
    style R4 fill:#bbf
    style R5 fill:#bbf
    style R6 fill:#bbf
    style R7 fill:#bbf
```

### 3.2 Responsibility Distribution Legend

| Color | Meaning | Executor |
|-------|---------|----------|
| 🟩 Green | Human-led | Developer |
| 🟩/🟦 Yellow | Collaborative | Developer + Agent |
| 🟦 Blue | Agent-led | AI Agent |

---

## 4. Agent Management Techniques

### 4.1 Four Core Technologies

```mermaid
graph TB
    subgraph "Agent Management Techniques"
        A[Agent Behavior Files<br/>CLAUDE.md/cursorrules/AGENTS.md]
        B[Hooks<br/>Event-driven Scripts]
        C[Commands<br/>Frequently-used Prompts]
        D[Subagents<br/>Runtime Delegation]
    end

    A --> |Static Config| E[Agent Behavior Guidance]
    B --> |Dynamic Control| F[Deterministic Execution]
    C --> |Efficiency Boost| G[Reuse Workflows]
    D --> |Capability Extension| H[Multi-Agent Collaboration]

    style A fill:#bfb
    style B fill:#bbf
    style C fill:#f9f
    style D fill:#f55
```

### 4.2 Hooks

> **Definition**: Deterministic scripts that run on predefined event types

```mermaid
sequenceDiagram
    participant User as User
    participant Agent as Agent
    participant Hook as Hook Script
    participant Tool as Tool

    Note over User,Tool: PreToolUse Hook
    User->>Agent: Request task execution
    Agent->>Hook: PreToolUse triggered
    Hook->>Hook: Validate/modify parameters
    Hook-->>Agent: Allow/deny
    Agent->>Tool: Execute tool

    Note over User,Tool: PostToolUse Hook
    Tool-->>Agent: Return result
    Agent->>Hook: PostToolUse triggered
    Hook->>Hook: Process/validate result
    Hook-->>Agent: Processing complete
    Agent-->>User: Return response
```

**Hook Types:**

| Hook Type | Trigger Time | Typical Use |
|-----------|--------------|-------------|
| `PreToolUse` | Before tool use | Validate parameters, add constraints |
| `PostToolUse` | After tool use | Validate results, logging |
| `UserPromptSubmit` | When user submits prompt | Input preprocessing |
| `PreCompact` | Before context compaction | Preserve key information |
| `...` | More types | Continuously expanding |

### 4.3 Commands

> **Definition**: Provide frequently-used prompts as files for Agent to execute

**Use Cases:**

| Scenario | Description |
|----------|-------------|
| Running Tests | Automated test workflows |
| Code Review | Standardized review process |
| Git Operations | Standardized commit, push |
| Deployment | Automated deployment steps |

**Benefits:**
- Reuse high-frequency workflows
- Team standardization
- Reduce repetitive input

### 4.4 Subagents

> **Definition**: Runtime delegation, creating independent developer personas

```mermaid
graph TB
    subgraph "Subagent Architecture"
        Main[Main Agent]

        Main --> FE[Frontend Subagent<br/>Focus on UI/UX]
        Main --> BE[Backend Subagent<br/>Focus on API/Data]
        Main --> Test[Testing Subagent<br/>Focus on Tests]
        Main --> Doc[Documentation Subagent<br/>Focus on Docs]
    end

    style Main fill:#f9f
    style FE fill:#bfb
    style BE fill:#bbf
    style Test fill:#ff9
    style Doc fill:#9ff
```

**Purposes of Subagents:**

1. **Create Different Developer Personas**
   - Frontend specialist
   - Backend specialist
   - Testing specialist
   - Documentation specialist

2. **Cleanly Separate Contexts**
   - Independent workflow contexts
   - Avoid context pollution

3. **Provide Customization**
   - Custom system prompts
   - Dedicated tool sets
   - Separate context windows

4. **Move Toward Agents Managing Agents**
   - Hierarchical management
   - Specialized division of labor

**Reference Resources:**
- [Awesome Claude Agents](https://github.com/vijaythecoder/awesome-claude-agents)
- [SuperClaude Framework](https://github.com/SuperClaude-Org/SuperClaude_Framework)

### 4.5 Agent Behavior Files

| File | Tool | Purpose |
|------|------|---------|
| `CLAUDE.md` | Claude Code | Context auto-loaded by Claude |
| `cursorrules` | Cursor | Cursor rule configuration |
| `AGENTS.md` | General | Open format Agent instructions |

---

## 5. Claude Code Deep Guide

### 5.1 Claude Code's Approach

```mermaid
graph TB
    subgraph "Claude Code Core Philosophy"
        W[Works Everywhere]
        T[Terminal-Native]
        L[Low-level Model Access]
        I[Infinitely Hackable]
    end

    style W fill:#bfb
    style T fill:#bbf
    style L fill:#f9f
    style I fill:#ff9
```

### 5.2 Covers the Entire SDLC

```mermaid
graph LR
    subgraph "Software Development Lifecycle"
        D1[Discover] --> D2[Design]
        D2 --> D3[Build]
        D3 --> D4[Deploy]
        D4 --> D5[Support & Scale]
    end

    D1 -.->|Explore codebase & history| E1[Search docs<br/>Onboard & learn]
    D2 -.->|Plan project| E2[Develop tech specs<br/>Define architecture]
    D3 -.->|Implement code| E3[Write & execute tests<br/>Create commits/PRs]
    D4 -.->|Automate CI/CD| E4[Configure envs<br/>Manage deployments]
    D5 -.->|Debug errors| E5[Monitor usage<br/>Large-scale refactor]
```

**Using your team's CLI tools**: git, docker, bq, etc. - focus on solutions, not syntax.

### 5.3 Multiple Interfaces

```mermaid
graph TB
    subgraph "Claude Code Interfaces"
        Terminal[Terminal]
        IDE[IDE]
        Web[Web & iOS]
        SDK[SDK]
    end

    subgraph "SDK Usage Examples"
        SDK_Example["$ claude -p 'what did i do this week?' --allowedTools Bash(git log:*) --output-format stream-json"]
        SDK_Pipe["$ get-gcp-logs | claude -p 'correlate errors + commits' --output-format=json | jq '.result'"]
    end

    SDK --> SDK_Example
    SDK --> SDK_Pipe
```

### 5.4 Installation

```bash
npm install -g @anthropic-ai/claude-code
```

### 5.5 Core Use Cases

#### Use Case 1: Codebase Q&A + Research

```mermaid
graph LR
    subgraph "Codebase Q&A & Research"
        Q1[Understand Code Structure]
        Q2[Track Git History]
        Q3[Understand Issue Fixes]
        Q4[Version Tracking]
        Q5[PR Verification]
        Q6[Work Summary]
    end
```

**Example Questions:**
```
> how do I make a new @app/services/ValidationTemplateFactory?
> why does recoverFromException take so many arguments? look through git history to answer
> why did we fix issue #18363 by adding the if/else in @src/login.ts api?
> in which version did we release the new @api/ext/PreHooks.php api?
> look at PR #9383, then carefully verify which app versions were impacted
> what did I ship last week?
```

#### Use Case 2: Write Code

| Mode | Description |
|------|-------------|
| **1-shot** | Single completion, suitable for simple tasks |
| **Sidekick** | Assistant mode, human-machine collaboration |
| **Prototype** | Rapid prototyping, iterative refinement |

#### Use Case 3: Integrate Tools & MCPs

```bash
# Add MCP Server
$ claude mcp add barley_server -- node myserver

# Use MCP
> use the barley mcp server to check for error logs
```

#### Use Case 4: Power Automation

Automate complex workflows, reduce repetitive work.

### 5.6 Workflow Adaptation to Tasks

```mermaid
graph TB
    subgraph "Explore-Plan Tasks"
        EP1[explore] --> EP2[plan] --> EP3[confirm] --> EP4[code] --> EP5[commit]
    end

    subgraph "Test-Driven Tasks"
        TD1[tests] --> TD2[commit] --> TD3[code] --> TD4[iterate] --> TD5[commit]
    end

    subgraph "Prototype Iteration Tasks"
        PI1[code] --> PI2[screenshot] --> PI3[iterate] --> PI1
    end
```

**Workflow Examples:**

**Explore-Plan Type:**
```
> figure out the root cause for issue #983, then propose a few fixes.
  Let me choose an approach before you code. ultrathink
```

**Test-Driven Type:**
```
> write tests for @utils/markdown.ts to make sure links render properly
  (note the tests won't pass yet, since links aren't yet implemented).
  then commit. then update the code to make the tests pass.
```

**Prototype Iteration Type:**
```
> implement [mock.png]. Then screenshot it with puppeteer and iterate
  till it looks like the mock.
```

### 5.7 Prototype Iteration Example

Demonstrating how Claude Code rapidly iterates UI design:

```
> make it so instead of todos showing up as they come in, we hide the
  tool use and result for todos, and render a fixed todo list above
  the input. title it "/todo (1 of 3)" in grey

> actually don't show a todo list at all, and instead render the tool
  uses inline, as bold headings when the model starts working on a todo

> also add a todo pill under the text input, similar to bg tasks

> actually undo both the pill and headings. instead, make the todo list
  render to the right of the input, vertically centered with a grey divider

> instead of showing todos above the input, merge them into the spinner.
  show the current todo as the spinner message in active verb form
```

---

## 6. Best Practices

### 6.1 Safeguards

```mermaid
graph TB
    subgraph "Best Practices Framework"
        B1[Careful Backstops]
        B2[Auditability]
        B3[Model Selection]
        B4[Regular Checkpoints]
    end

    B1 --> B1a[Tests in codebase]
    B1 --> B1b[CI/CD best practices]

    B2 --> B2a[Label every Agent's diff]
    B2 --> B2b[Retain operation logs]

    B3 --> B3a[Complex tasks: More guidance]
    B3 --> B3b[Simple tasks: Less intervention]

    B4 --> B4a[Frequent commits]
    B4 --> B4b[Branch strategy]
```

### 6.2 Core Principles

| Principle | Description |
|-----------|-------------|
| **Safeguards** | Tests, CI/CD, security checks |
| **Auditability** | Label every Agent's diff, retain logs |
| **Model Selection** | Use different models for different tasks |
| **Regular Checkpoints** | Frequent commits for easy rollback |

### 6.3 Open Questions

1. **Automating Research Phase**
   > How can we automate the first 10-20% research phase of any task?

2. **Task Queue Management**
   > How to maintain a queue of pending tasks (easier for one-off changes)?

---

## 7. Anthropic Internal Practices Case Study

> Based on **How Anthropic Uses Claude Code** reading material

### 7.1 Team Use Cases for Claude Code

```mermaid
graph TB
    subgraph "Anthropic Team Applications"
        DI[Data Infrastructure<br/>Kubernetes debugging<br/>Data workflow automation<br/>Onboarding code navigation]
        PD[Product Development<br/>Feature development<br/>Bug fixes<br/>Refactoring]
        SE[Security Engineering<br/>Security code review<br/>Vulnerability fixes]
        DS[Data Science<br/>Data analysis<br/>Visualization]
        API[API Team<br/>API doc generation<br/>SDK development]
        GM[Growth Marketing<br/>A/B test analysis<br/>Marketing automation]
        PX[Product Design<br/>Design system docs<br/>Prototype iteration]
    end
```

| Team | Use Cases |
|------|-----------|
| **Data Infrastructure** | Kubernetes debugging, data workflow automation, onboarding code navigation |
| **Product Development** | Feature development, bug fixes, refactoring |
| **Security Engineering** | Security code review, vulnerability fixes |
| **Data Science** | Data analysis, visualization |
| **API Team** | API documentation generation, SDK development |
| **Growth Marketing** | A/B test analysis, marketing automation |
| **Product Design** | Design system documentation, prototype iteration |

### 7.2 Best Practices Highlights (from Anthropic Teams)

1. **Detailed CLAUDE.md files** - More detailed documentation = better Claude Code performance
2. **Use MCP servers** - Extend Claude Code capabilities
3. **Screenshot assistance** - Use screenshots to show expected interface
4. **Incremental development** - Implement one step at a time
5. **End-of-session documentation** - Summarize completed work, improve workflows

---

## 8. Key Lessons

```mermaid
graph TB
    subgraph "Three Key Lessons"
        L1[Build for the model<br/>six months from now]
        L2[Be ready to evolve]
        L3[Ask not what the model<br/>can do for you]
    end

    style L1 fill:#f9f
    style L2 fill:#bbf
    style L3 fill:#bfb
```

### 8.1 Core Insights

1. **Build for the model six months from now**
   - Model capabilities are rapidly improving
   - Today's designs should consider future capabilities

2. **Be ready to evolve**
   - Tools and methodologies are changing rapidly
   - Maintain learning and adaptation abilities

3. **Ask not what the model can do for you**
   - Think about how to provide better context for the model
   - Proactively optimize workflows

### 8.2 Productivity Trends

- **Programming Language Productivity**: Increasing exponentially (AI-driven)
- **IDE Productivity**: Following similar exponential growth
- **Verification Methods**: AI-driven testing is becoming mainstream

---

## 9. Practice Exercises

### Exercise 1: Configure CLAUDE.md
Create a project CLAUDE.md containing:
- Project introduction
- Common commands
- Code style
- Testing instructions

### Exercise 2: Use Claude Code
1. Install Claude Code
2. Explore codebase
3. Try writing code
4. Practice different workflow patterns

### Exercise 3: Add MCP
Try adding an MCP Server:
```bash
claude mcp add barley_server -- node myserver
```

### Exercise 4: Configure Hooks
Create a PreToolUse hook to validate before file modifications.

### Exercise 5: Use Subagents
Try creating specialized subagent configurations for different tasks.

---

## Lecture Materials

### Lecture 7: How to be an Agent Manager
- [Slides (PDF)](../slides/week4-lecture1-agent-manager.pdf)
- **Guest Speaker**: Boris Cherny, Anthropic (Creator of Claude Code)
- **Date**: 10/17/25

### Lecture 8: Welcome to Claude Code
- [Slides (PDF)](../slides/week4-lecture2-claude-code.pdf)
- **Speaker**: Boris Cherny
- **Core**: Claude Code architecture, use cases, best practices

---

## Reading Materials

### Required
1. **[Claude Code Official Documentation](https://docs.anthropic.com/en/docs/claude-code)**
2. **[How Anthropic Uses Claude Code (PDF)](../readings/how-anthropic-uses-claude-code.pdf)**

### Recommended Resources
1. **[Awesome Claude Agents](https://github.com/vijaythecoder/awesome-claude-agents)**
2. **[SuperClaude Framework](https://github.com/SuperClaude-Org/SuperClaude_Framework)**

---

## Assignment

**[Chapter 4 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week4)**

Practice Agent management techniques and create custom workflows.

---

## Next Chapter

[Next Chapter: Chapter 5](./chapter5.md)

---
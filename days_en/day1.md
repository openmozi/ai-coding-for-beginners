# Chapter 1: Programming LLMs and AI Development

## Course Overview

In the age of large language models, software development is undergoing a revolutionary change. This course will help you master modern AI programming tools and understand best practices for AI-assisted development.

### Learning Objectives
- Understand the fundamentals of Large Language Models (LLMs)
- Master efficient prompt engineering techniques
- Identify core skills for Human-agent engineering
- Understand LLM capability boundaries

---

## 1. Why This Course?

> "You won't be replaced by AI. You'll be replaced by a competent engineer who knows how to use AI."

AI programming is the core skill for future software engineers. Engineers who don't know AI will be replaced by engineers who do. But this is **NOT a "vibe coding"** course—don't blindly trust AI output. Human-agent engineering is the core.

> Prompts are the lingua franca for getting LLMs to do what we want and also effectively programming them
>
> — Andrej Karpathy

### Bad News vs Good News

| News | Content |
|------|---------|
| **Bad News** | Windsurf team (AI coding company acquisition) |
| **Good News** | Developers can be more productive than ever before; AI engineers can pick up tech stacks and tools at an unprecedented pace |

---

## 1.1 Course Information

| Item | Content |
|------|---------|
| Course Code | CS146S |
| School | Stanford University, Fall 2025 |
| Instructor | Mihail Eric |
| Course Website | themodernsoftware.dev |

### Course Schedule
- **Class Time**: Mon/Fri 8:30-9:20 am PT
- **Deliverables**: 9 assignments (1/week) + 1 final project
- **Grading**: Project 80% / Assignments 15% / Participation 5%

### Instructor Bio
Mihail Eric is a Stanford undergrad/grad who has:
- Led AI at a stealth startup in the sales space
- Built first LLMs at Amazon Alexa
- Founded and sold an ML education startup
- Founded a YC-backed AI coding company

### Course Assistant
- Febie Lin

### Guest Lectures
The course includes guest lectures from founders leading top AI developer startups:
- Hundreds of millions raised, billions in valuation
- Don't miss these talks!

### Human-agent Engineering Core Skills
1. **Read and review a lot of code** - Learn to discern good from bad code
2. **Have good taste** - Understand what excellent software looks like
3. **Experiment aggressively** - No one has standard answers, everyone is exploring

### Key Insights
- LLMs are only as good as you are (Good context leads to good code)
- If you can't understand your codebase, neither will an LLM

---

## 2. LLM Fundamentals

### What is an LLM?
LLM (Large Language Models) are **autoregressive models** for next-token prediction.

```
Input Text → Tokenize → Embedding → Transformer Layers (12-96+) → Output Prediction
```

#### Transformer Layers
- Use self-attention mechanism (reference Viswani et al.)
- 12-96+ Transformer layers
- Convert tokens into fixed-dimensional numerical vectors (~1-3K dimensions)

#### Embedding
Convert text tokens into fixed-dimensional numerical vectors.

---

## 3. LLM Training Process

### Three Training Stages

| Stage | Name | Data Size | Goal |
|-------|------|-----------|------|
| Stage 1 | Self-supervised Pretraining | 100B - 1T+ tokens | Learn language concepts |
| Stage 2 | Supervised Finetuning | 10K - 100K pairs | Follow instructions |
| Stage 3 | Preferencing Tuning | 10K - 100K comparisons | Align with human preferences |

### Stage 1: Pretraining
- Use massive public data (Common Crawl, Wikipedia, StackExchange, GitHub)
- Learn basic concepts and patterns of language
- **Example**: "Write a for loop" → "that could be used in a piece of code"

### Stage 2: Supervised Finetuning (SFT)
- Use high-quality instruction-response pairs
- Teach model to follow human instructions
- **Example**: "what is the capital of Croatia" → "Zagreb is the capital"

### Stage 3: Preferencing Tuning
- Collect pairs of outputs for same prompt
- Train reward model to predict preferred output
- Align with human preferences (helpfulness, correctness, readability)
- **Example**: "Write a for loop" → "for idx in range(10):"

#### Reasoning Models
- Extend training with chain-of-thought reasoning traces
- Integrate tool-use capability
- Learn to evaluate reasoning processes through reinforcement learning
- Learn to backtrack and other reasoning steps

#### Model Size Reference
- GPT-3 / Claude 3.5 Sonnet: ~175B parameters
- LLaMA 3.1: 405B parameters
- GPT-4: ~1.8T parameters

---

## 4. LLM Capabilities and Limitations

### Strengths
- **Expert-level code completion** - Expert-level code completion
- **Code understanding** - Code understanding
- **Code fixing** - Code fixing

### Limitations
| Limitation | Description | Solution |
|------------|-------------|----------|
| Hallucinations | Generating non-existent/out-of-date APIs | Robust context engineering |
| Context window limits | ~100-200K tokens, but not all are created equal | Selective context |
| Latency | Seconds to minutes per request | Plan and delegate accordingly |
| Cost | $1-3/million input tokens, $10+/million output tokens | Optimize prompt length |

---

## 5. Prompt Engineering Techniques

### Prompt Engineering Background
Prompting is both an art and a science. The black-box nature of LLMs means there's some "LLM whispering"... but there are established techniques that have empirically improved LLM performance.

### Zero-shot Prompting
Ask the LLM to do a thing without examples.

**Example**:
```
Write me a Rust for-loop that iterates over a list of strings for every, printing every value in an even index
```

### K-shot Prompting
Provide k examples (1, 3, 5), also called "in-context learning", suitable for tasks requiring specific format.

**Example**:
```
Write a for-loop iterating over a list of strings using the naming convention in our repo. Here are some examples of how we typically format variable names.

<example>var StRaRrAy = ['cat', 'dog', 'wombat']</example>
<example>def func CaPiTaLiZeStR = () => {}</example>
```

### Chain-of-Thought (CoT)
- **Multi-shot CoT**: Show reasoning step examples
- **Zero-shot CoT**: Add "Let's think step-by-step" or prompt for reasoning in explicit <reasoning> tags
- Best for multi-step logical tasks (programming, math)

### Role Prompting
Specify model role to enhance output quality.

**Role Prompting Examples**:
```
You are a helpful assistant that loves programming at the level of a senior software developer and is very detailed and pedantic in your answers.
```
```
You are a Gen Z digital bestie. Always sound like you're texting on Snapchat at 2am.
```

### System Prompt vs User Prompt

| Type | Description |
|------|-------------|
| **System Prompt** | First message defining LLM overall behavior and rules (usually not seen by end user) |
| **User Prompt** | User's actual request/instruction |
| **Assistant** | What the LLM actually generates |

### Best Practices

#### Prompt Improvement
- Use [Claude Prompt Improver](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/prompt-improver)
- Give the prompt to someone with minimal context; if they're confused, an LLM will be too

#### Structured Prompting
```
Here are the logs:
<log>LOG MESSAGE</log> and the stack trace:
<error>STACK TRACE</error>
```

#### Be Explicit
- Specify language, tech stack, libraries, constraints

#### Decompose Tasks
- Break complex tasks into simple steps

---

## 6. Practice Exercises

### Exercise 1: Try Different Prompting Techniques
Using Claude or other LLMs:
1. Zero-shot: "Write a function to check if a number is prime"
2. K-shot: Provide examples then have LLM output in same format
3. CoT: Add "Let's think step-by-step" and observe output changes

### Exercise 2: Role Prompting
Try different role prompts and compare output quality:
- "You are a junior developer..."
- "You are a senior software architect..."
- "You are a Gen Z digital bestie..."

### Exercise 3: Structured Prompting
Provide logs and error messages, observe how LLM parses and responds.

### Exercise 4: Use Prompt Improver
Use Claude Prompt Improver to optimize your prompts and observe improvements.

---

## 7. Course Learning Path

| Day | Topic |
|-----|-------|
| Day 1 | LLM Basics + Prompt Engineering |
| Day 2 | Coding Agent + MCP |
| Day 3 | AI IDE + Sync/Async |
| Day 4 | Agent Management + Claude Code |
| Day 5 | AI Developer Product Design |
| Day 6 | Testing + Security |
| Day 7 | Code Review |
| Day 8 | AI App Building |
| Day 9 | AI DevOps |
| Day 10 | Future Outlook |

---

## Lecture Materials

### Lecture 1: Introduction and How LLMs are Made
- [Slides (PDF)](../slides/week1-lecture1-introduction.pdf)
- **Instructor**: Mihail Eric

### Lecture 2: Power Prompting for LLMs  
- [Slides (PDF)](../slides/week1-lecture2-power-prompting.pdf)
- **Reference**: Andrej Karpathy's prompting background

---

## Reading Materials

### Required
1. **[Prompt Engineering Guide](https://www.promptingguide.ai/techniques)** - Comprehensive prompt engineering techniques guide
2. **[Deep Dive into LLMs (YouTube)](https://www.youtube.com/watch?v=7xTGNNLPyMI)** - LLM deep dive

### Optional
3. **[Prompt Engineering Overview](https://cloud.google.com/discover/what-is-prompt-engineering)** - Google Cloud prompt engineering overview

---

## Assignment

### LLM Prompting Playground
**[Day 1 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week1)**

Master LLM prompting techniques through practice.

---

## Key Concepts

| Term | Meaning |
|------|---------|
| **Tokenization** | How text is split into tokens |
| **Context Window** | Length of context model can process |
| **Temperature** | Parameter controlling output randomness |
| **Embedding** | Converting tokens to fixed-dimensional numerical vectors |
| **Human-agent Engineering** | Human engineers as AI's manager and decision-maker |
| **Autoregressive Models** | Models for next-token prediction |
| **Self-attention** | Self-attention mechanism |
| **In-context Learning** | Context learning, i.e., K-shot Prompting |

---

## Tomorrow's Preview

Day 2 will dive into Coding Agents architecture, learning how to build your own coding agents.

---


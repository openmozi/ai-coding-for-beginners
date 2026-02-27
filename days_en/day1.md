# Chapter 1: Introduction to Coding LLMs and AI Development

## Course Overview

In the era of Large Language Models, software development is undergoing a revolutionary change. This course will help you master modern AI programming tools and understand best practices for AI-assisted development.

### Learning Objectives
- Understand the fundamentals of Large Language Models (LLMs)
- Master efficient prompt engineering techniques
- Understand Human-agent engineering core skills
- Understand LLM capability boundaries

---

## 1. Why Learn This?

> "You won't be replaced by AI. You'll be replaced by a competent engineer who knows how to use AI."

AI programming is the core skill for future software engineers. But this is NOT a "vibe coding" course - don't blindly trust AI output. Human-agent engineering is the key.

### Human-agent Engineering Core Skills
1. **Read and review lots of code** - learn to discern good from bad code
2. **Have good taste** - understand what excellent software looks like
3. **Experiment aggressively** - no one has standard answers

### Key Insights
- LLMs are only as good as you are (Good context leads to good code)
- If you can't understand your codebase, neither will an LLM

---

## 2. LLM Training Process

### Three Training Stages

| Stage | Name | Data Amount | Goal |
|-------|------|-------------|------|
| Stage 1 | Self-supervised Pretraining | 100B - 1T+ tokens | Learn language concepts |
| Stage 2 | Supervised Finetuning | 10K - 100K pairs | Follow instructions |
| Stage 3 | Preferencing Tuning | 10K - 100K comparisons | Align with human preferences |

#### Stage 1: Pretraining
```
Text Input → Tokenize → Embedding → Model Processing → Output
```
- Use massive public data (Common Crawl, Wikipedia, StackExchange, GitHub)

#### Stage 2: Supervised Finetuning (SFT)
- Use high-quality instruction-response pairs

#### Stage 3: Preferencing
- Collect multiple output pairs for same prompt
- Train reward model to predict preferred output

### Reasoning Models
- Add chain-of-thought reasoning traces
- Integrate tool-use capability

### Model Scale Reference
- GPT-3 / Claude 3.5 Sonnet: ~175B parameters
- LLaMA 3.1: 405B parameters
- GPT-4: ~1.8T parameters

---

## 3. LLM Capabilities and Limitations

### Strengths
- **Expert-level code completion**
- **Code understanding**
- **Code fixing**

### Limitations

| Limitation | Description | Solution |
|------------|-------------|----------|
| Hallucinations | Generate non-existent APIs | Context engineering |
| Context window limits | ~100-200K tokens | Select best context |
| Latency | Seconds to minutes | Plan according to task |
| Cost | $1-3/M input, $10+/M output | Optimize prompt length |

---

## 4. Prompt Engineering Techniques

### Zero-shot Prompting
Directly ask LLM to perform task without examples.

### K-shot Prompting
Provide k examples (1, 3, 5), also called "in-context learning".

### Chain-of-Thought (CoT)
- **Multi-shot CoT**: show reasoning step examples
- **Zero-shot CoT**: add "Let's think step-by-step"
- Good for multi-step logical tasks

### Role Prompting
Specify model role to enhance output quality:
```
You are a helpful assistant that loves programming at the level
of a senior software developer.
```

### System Prompt vs User Prompt

| Type | Description |
|------|-------------|
| **System Prompt** | First message, defines LLM overall behavior |
| **User Prompt** | User's actual request |
| **Assistant** | LLM's generated response |

### Best Practices
1. **Structured prompts**:
```
Here are the logs:
<log>LOG MESSAGE</log>
and the stack trace:
<error>STACK TRACE</error>
```
2. Be specific - specify language, tech stack
3. Break complex tasks into simple steps
4. Use Claude Prompt Improver

---

## 5. Practice Exercises

### Exercise 1: Try Different Prompt Techniques
Use Claude or other LLM to try:
1. Zero-shot: "Write a function to check if a number is prime"
2. K-shot: Provide examples then ask for same format
3. CoT: Add "Let's think step-by-step"

### Exercise 2: Role Prompting
Try different role prompts and compare outputs:
- "You are a junior developer..."
- "You are a senior software architect..."

---

## 6. Course Learning Path

| Day | Topic |
|-----|-------|
| Day 1 | LLM Basics + Prompting |
| Day 2 | Coding Agent + MCP |
| Day 3 | AI IDE + Sync/Async |
| Day 4 | Agent Management + Claude Code |
| Day 5 | AI Dev Product Design |
| Day 6 | Testing and Security |
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

---

## Reading Materials

### Required
1. **[Prompt Engineering Guide](https://www.promptingguide.ai/techniques)**
2. **[Deep Dive into LLMs (YouTube)](https://www.youtube.com/watch?v=7xTGNNLPyMI)**

---

## Assignment

**[Day 1 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week1)**

---

## Tomorrow's Preview

Day 2 will dive into Coding Agents architecture, learning how to build your own coding agent.

---

*Learning Time: 8-10 hours*

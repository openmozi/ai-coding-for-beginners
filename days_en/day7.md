# Chapter 7: Modern Software Support

## Course Overview

> "Software code review is one of the highest leverage activities you can do to become a better engineer"

Code Review is the highest leverage activity. AI Code Review is more important than ever.

### Learning Objectives
- Understand the importance of Code Review
- Master Code Review best practices
- Learn AI Code Review tool usage
- Understand limitations of AI Code Review

---

## 1. Code Review Statistics

| Metric | Data |
|--------|------|
| Code Review error detection rate | 55-60% |
| Error rate without Code Review | 4.5 errors/100 lines |
| Error rate with Code Review | 0.82 errors/100 lines |
| AT&T case | 14% productivity increase, 90% defect reduction |
| Testing mode error detection rate | 25-45% |

**Source**: Coding Horror

---

## 2. What to Check in Code Review?

### Logic and Correctness
- Is the code logic correct?
- Are there bugs?
- Are edge cases handled?

### Readability and Maintainability
- Is the code clear and readable?
- Are names reasonable?
- Are functions too long?

### Performance
- Are there performance issues?
- Is the algorithm optimal?
- Are there unnecessary computations?

### Security
- Are there security vulnerabilities?
- Is input validation sufficient?
- Are there risks of sensitive data exposure?

### Best Practices
- Does it follow project conventions?
- Does it follow language/framework best practices?
- Is there duplicate code?

---

## 3. Good Code Review vs Bad Review

### Bad Review
> "This won't work"

### Good Review
> "I see your new method matches the existing style in this file, taking [X] parameters. Having that many parameters hurts readability and implies the function is doing too much. What do you think about refactoring this method and the existing ones in a later pull request to reduce how many parameters they take?"

**Source**: Blake Smith

---

## 4. AI Code Review Tools

### Available Tools

| Tool | Description |
|------|-------------|
| **Graphite** | AI Code Review platform, guest speaker for this course |
| **Greptile** | AI code review service |
| **CodeRabbit** | AI-driven code review |
| **Claude Code / Codex** | AI-assisted code review |

---

## 5. What Has AI Changed?

| Aspect | Changes |
|--------|----------|
| **Efficiency** | Quickly scan large amounts of code to find issues |
| **Consistency** | Apply same standards to all code |
| **Knowledge sharing** | Spread team best practices |
| **Reduced cognitive load** | Automate routine checks |
| **Continuous improvement** | System learns and improves over time |
| **Holistic understanding** | Better understanding of codebase |

**Sources**: Greptile, Graphite

---

## 6. Limitations of AI Code Review

### Limitations

| Limitation | Description |
|------------|-------------|
| **More configuration/setup** | Requires additional setup and learning |
| **False positives** | Need to continuously train the system |
| **Can't catch idioms** | Can't yet catch repo-specific idioms and best practices |
| **Complex logic** | Can't handle complex business logic and architecture decisions |
| **Security changes** | Must be extra cautious with security changes |
| **Edge cases** | Often misses edge cases |

> **Important Reminder**: Code Review with AI is more important than ever.
> You own the code that is merged and shipped, don't blame AI. AI is the assistant, you are the final responsible person.

---

## 7. Practice Exercises

### Exercise 1: Practice Code Review
Practice Code Review daily to build the habit.

### Exercise 2: Use AI-assisted Review
Use Graphite or Claude Code to assist Code Review.

### Exercise 3: Improve Review Quality
Learn to provide constructive Code Review feedback.

---

## Lecture Materials

### Lecture 13: AI Code Review
- [Slides (PDF)](../slides/week7-lecture1-code-review.pdf)
- **Guest Speaker**: Tomas Reimers, CPO of Graphite
- **Date**: 11/7/25

---

## Reading Materials

1. **[Code Reviews: Just Do It](https://blog.codinghorror.com/code-reviews-just-do-it/)**
2. **[How to Review Code Effectively](https://github.blog/developer-skills/github/how-to-review-code-effectively-a-github-staff-engineers-philosophy/)**

---

## Assignment

**[Week 7 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week7)**

Practice Code Review and develop code review skills.

---

## Tomorrow's Preview

Day 8 will discuss automated UI and app building, learning how AI is changing frontend development.

---


# Chapter 6: AI Testing and Security

## Course Overview

> "Software errors can dash user trust in a product/company and incur huge financial costs"

When an LLM is writing most of your code, you need extensive guardrails to prevent errors. Software quality in the AI era is more important than ever.

### Learning Objectives
- Understand traditional security threats and testing methods
- Master SAST, DAST, SCA and other security testing techniques
- Understand new AI Agent attack vectors
- Learn limitations of LLMs in security testing

---

## 1. Traditional Threat Landscape

### OWASP Top 10 Threats

| Threat Type | Description |
|-------------|-------------|
| SQL Injections | SQL injection attacks |
| Cross-site scripting (XSS) | Cross-site scripting attacks |
| Broken authentication | Authentication breakage |
| Insecure direct object references | Insecure direct object references |
| Security misconfigurations | Security configuration errors |
| Sensitive data exposure | Sensitive data leakage |

---

## 2. Vulnerability Detection Techniques

### SAST (Static Application Security Testing)
- **Type**: White box testing
- **Analysis**: Binaries and source code
- **Stage**: Early in SDLC (cheapest to identify and correct)
- **Technique**: Codebase pattern matching scan
- **Finds**: SQL injection, command injection, cross-site scripting

### DAST (Dynamic Application Security Testing)
- **Type**: Black box testing
- **Method**: Mimic real-world hackers to uncover vulnerabilities
- **Stage**: Throughout SDLC, fewer false positives
- **Techniques**:
  - Input fuzzing
  - Manipulating session tokens
  - Configuration/header testing
  - Brute force rate-limit tests

### SCA (Software Composition Analysis)
- **Analysis**: Deep analysis of open source packages used by application
- **Method**: Analyze package managers, infrastructure-as-code, pull images
- **Technique**: Scan for dependency vulnerabilities

### Testing Method Comparison

| Method | Type | Stage | Advantages |
|--------|------|-------|------------|
| SAST | White box | Early | Low cost, wide coverage |
| DAST | Black box | Entire SDLC | Fewer false positives, finds runtime issues |
| SCA | Dependency analysis | Build time | Check third-party library vulnerabilities |

---

## 3. What Has Changed?

### Shift Left Security
- "Shift left" security is more accessible than ever
- LLMs can be introduced in workflow to spot issues
- Automated penetration testing

### LLMs in Security Testing
- Automated code review
- Vulnerability detection
- Fix suggestions

---

## 4. New AI Agent Attack Vectors

| Attack Type | Description |
|-------------|-------------|
| **Prompt Injection** | Hidden or misleading instructions to make AI deviate from intended behavior |
| **Tool Misuse** | Deceptive prompts manipulate agent to abuse integrated tools |
| **Intent Breaking** | Manipulate agent's plan to redirect actions away from original intent |
| **Identity Spoofing** | Exploit compromised authentication to pose as legitimate agents |
| **Code Attacks** | Exploit agent's ability to execute code to gain unauthorized access to execution environment |

---

## 5. Limitations of LLMs in Security Testing

| Limitation | Description |
|------------|-------------|
| **High false positive rate** | Claude Code/Codex false positive rate 50-100%, depending on vulnerability type |
| **Nondeterministic analysis** | Same prompt runs multiple times get different results - how do you know you're catching all vulnerabilities? |
| **Context rot** | Not all context is created equally |
| **Compaction** | Summarization leads to information loss |
| **Unrealistic benchmarks** | Existing benchmarks are often unrealistic, hard to evaluate LLMs |

### Comparison with Traditional SAST
- AI SAST false positive rate: 50-100% (depends on vulnerability)
- Traditional SAST false positive rate: 50%+

---

## 6. Open Questions

| Questions |
|-----------|
| How to reduce false positives and hallucinations in vulnerability detection? |
| How to verify LLM-generated patches are secure and don't introduce regressions? |
| How can LLMs explain why they flag a vulnerability or propose a fix? |
| What are the right benchmarks for measuring LLMs' AppSec performance? |
| How should LLMs be embedded in CI/CD without overwhelming teams with noise? |
| Who is accountable if an AI-generated patch introduces a vulnerability? |

---

## 7. Practice Exercises

### Exercise 1: Use SAST Tools
1. Install Semgrep
2. Scan a code repository
3. Analyze scan results

### Exercise 2: Understand AI Security
1. Try prompt injection attacks
2. Learn how to defend

### Exercise 3: Security Code Review
Use AI tools for security code review

---

## Lecture Materials

### Lecture 11: AI Testing and Security
- [Slides (PDF)](../slides/week6-lecture1-ai-qa-sast-dast.pdf)
- **Guest Speaker**: Isaac Evans, CEO of Semgrep
- **Date**: 10/31/25

---

## Reading Materials

1. **[Semgrep Documentation](https://semgrep.dev/docs)**
2. **[OWASP Top 10](https://owasp.org/www-project-top-ten/)**

---

## Assignment

**[Week 6 Assignment](https://github.com/mihail911/modern-software-dev-assignments/blob/master/week6/assignment.md)**

Learn to write secure AI code and implement security testing.

---

## Tomorrow's Preview

Day 7 will discuss modern software support, learning AI Code Review practices.

---


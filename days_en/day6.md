# Day 6: AI Testing and Security

## Course Overview

> "Software errors can dash user trust and incur huge financial costs"

When LLMs write most of your code, you need extensive guardrails. Software quality matters more than ever.

---

## 1. Traditional Threat Landscape

| Threat Type |
|-------------|
| SQL Injections |
| Cross-site scripting (XSS) |
| Broken authentication |
| Security misconfigurations |
| Sensitive data exposure |

---

## 2. Vulnerability Detection Techniques

### SAST (Static Application Security Testing)
- White box testing
- Analyze source code
- Early in SDLC

### DAST (Dynamic Application Security Testing)
- Black box testing
- Mimic real hackers
- Throughout SDLC

### SCA (Software Composition Analysis)
- Open source package analysis
- Third-party vulnerability checking

### Comparison

| Method | Type | Stage |
|--------|------|-------|
| SAST | White box | Early |
| DAST | Black box | Entire SDLC |
| SCA | Dependency | Build time |

---

## 3. New AI Agent Attack Vectors

| Attack Type |
|-------------|
| **Prompt Injection** |
| **Tool Misuse** |
| **Intent Breaking** |
| **Identity Spoofing** |
| **Code Attacks** |

---

## 4. LLM Limitations in Security Testing

| Limitation |
|------------|
| High false positive rates (50-100%) |
| Non-deterministic analysis |
| Context rot |

---

## Lecture Materials

### Lecture 11: AI Testing and Security
- [Slides (PDF)](slides/week6-lecture1-ai-qa-sast-dast.pdf)
- **Guest Speaker**: Isaac Evans, CEO of Semgrep

---

## Reading Materials

1. **[Semgrep Docs](https://semgrep.dev/docs)**
2. **[OWASP Top 10](https://owasp.org/www-project-top-ten/)**

---

## Assignment

**[Week 6 Assignment](https://github.com/mihail911/modern-software-dev-assignments/blob/master/week6/assignment.md)**

---

## Tomorrow's Preview

Day 7 will explore modern software support, learning AI Code Review practices.

---

*Learning Time: 10-12 hours*

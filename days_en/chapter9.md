# Chapter 9: Agent Deployment and Operations

## Course Overview

> "Monitoring software systems in production remains a mission-critical task"

Coding represents just 30 percent of engineering time. The harder 70 percent is running that code.

### Learning Objectives
- Understand traditional SRE responsibilities
- Master the four golden monitoring signals
- Learn incident response playbook
- Understand characteristics and limitations of AI SRE

---

## 1. Traditional SRE Responsibilities

| Responsibility | Description |
|----------------|-------------|
| **Operational monitoring** | On-call, troubleshooting, infrastructure management and security |
| **Incident resolution** | Piecing together information from many different sources and teams |
| **Maintaining runbooks** | Maintaining often outdated troubleshooting manuals |
| **Burnout** | SRE fatigue due to on-call shifts |

### Modern Challenges
- Shift to cloud-native architectures
- Containerized workloads and Kubernetes
- Introduced more data, dependencies, and complexity across systems

---

## 2. Four Golden Monitoring Signals

| Signal | Description |
|--------|-------------|
| **Latency** | Latency |
| **Errors** | Errors |
| **Traffic** | Traffic (requests/sec) |
| **Saturation** | Saturation |

### Monitor Production Traces
- Use traces to monitor production

---

## 3. Incident Response Playbook

### Scenario
> At 3:12 am you get a ping from PagerDuty that you're seeing a spike in 500s on your database queries. What do we do?

### Response Steps

```
1. Acknowledge and assess
2. Check DB + app
3. Identify recent changes
4. Localize blast radius
5. Execute mitigations
6. Stabilize + monitor
7. Communicate
8. Document
```

### Key Metrics

| Metric | Description |
|--------|-------------|
| **MTTR** | Mean-time-to-repair |
| **On-call count** | How many engineers are pulled into incident |
| **SLA** | Service Level Agreement reported to customers |

---

## 4. Traditional Tools

### Existing AI SRE Tools
- Resolve AI (guest lecture)
- DataDog Bits AI Agent
- Splunk Observability Assistant

---

## 5. Characteristics of AI SRE

> "AI SRE" = Agentic system across observability stack and clouds

| Characteristic | Description |
|----------------|-------------|
| **Dynamic knowledge graph mapping** | Real-time understanding of system component relationships |
| **Agentic system across observability stack and clouds** | Cross-platform intelligent monitoring |
| **Real-time narratives** | Generate real-time narratives of what's happening |
| **Root cause analysis** | Pinpoint likely root causes with supporting evidence |
| **Fix recommendations** | Recommend prescriptive remediation steps |
| **Explainability and auditability** | Heavy emphasis on explainability and auditability of predictions/reasoning |

---

## 6. What Has AI Changed?

### Knowledge Scaling
AI promises to scale out organizational and service level knowledge:
- Information is not siloed to the only engineers who know undocumented dependencies, brittle legacy services, and quirks that only surface during high-stakes incidents

### Development Process Changes
- Automation reduces review time and catches issues early
- Developers learn best practices through AI suggestions
- AI applies same standards across all code reviews
- AI handles routine checks, letting humans focus on complex logic
- AI systems improve over time with more data
- Modern AI code review tools go deeper, offering contextual analysis and pattern recognition

---

## 7. Limitations of AI SRE

| Limitation | Description |
|------------|-------------|
| **Incident complexity** | Limited complexity of incidents that can be resolved |
| **Production stack heterogeneity** | Diversity of modern production stacks |
| **Code remediation** | Ability to remediate actual code based on what has been detected |
| **Monitoring gardening** | Good root cause analysis requires good monitoring maintenance |
| **Security risk** | Could be a new attack vector |

### End Goal
- All providers starting with root cause analysis
- End goal is code remediation

---

## 8. Practice Exercises

### Exercise 1: Learn Monitoring Basics
1. Understand the four golden monitoring signals
2. Explore a monitoring tool (e.g., DataDog)

### Exercise 2: Incident Response Drill
1. Simulate a simple incident
2. Follow playbook steps to respond

### Exercise 3: Explore AI SRE Tools
1. Learn about Resolve AI
2. Explore DataDog Bits AI Agent

---

## Lecture Materials

### Lecture 17: Incident response and DevOps
- [Slides (PDF)](../slides/week9-lecture1-incident-response.pdf)

### Lecture 18: Guest Speaker - Resolve AI
- **Guest Speakers**: Mayank Agarwal (CTO), Milind Ganjoo
- **Date**: 11/21/25

---

## Reading Materials

1. **[Introduction to Site Reliability Engineering](https://sre.google/sre-book/introduction/)**
2. **[Observability Basics](https://last9.io/blog/traces-spans-observability-basics/)**

---

## Assignment

**[Week 9 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week9)**

Practice AI-assisted incident response process.

---

## Next Chapter

[Next Chapter: Chapter 10](./chapter10.md)

---

# Day 6: AI Testing and Security
# 第六天：AI 测试与安全

## 课程概述

> "Software errors can dash user trust in a product/company and incur huge financial costs"

当 LLM 编写大部分代码时，需要广泛的护栏来防止错误。AI 时代的软件质量比以往任何时候都更重要。

---

## 1. 传统威胁 landscape

| 威胁类型 | 描述 |
|----------|------|
| SQL Injections | SQL 注入攻击 |
| Cross-site scripting (XSS) | 跨站脚本攻击 |
| Broken authentication | 认证破损 |
| Security misconfigurations | 安全配置错误 |
| Sensitive data exposure | 敏感数据泄露 |

---

## 2. 漏洞检测技术

### SAST（静态应用安全测试）
- **White box testing** - 白盒测试
- 分析源代码
- **在 SDLC 早期进行**，发现和修复成本最低
- 技术：代码库模式匹配扫描

### DAST（动态应用安全测试）
- **Black box testing** - 黑盒测试
- 模拟真实世界黑客行为
- 贯穿整个 SDLC，误报较少
- 技术：Input fuzzing、Session token 操作、配置测试

### SCA（软件组成分析）
- 深度分析应用使用的开源软件包
- 检查第三方库漏洞

### 测试方法对比

| 方法 | 类型 | 阶段 | 优点 |
|------|------|------|------|
| SAST | White box | 早期 | 成本低，覆盖广 |
| DAST | Black box | 整个 SDLC | 误报少，发现运行时问题 |
| SCA | 依赖分析 | 构建时 | 检查第三方库漏洞 |

---

## 3. AI Agent 新型攻击向量

| 攻击类型 | 描述 |
|----------|------|
| **Prompt Injection** | 隐藏或误导性指令使 AI 偏离预期行为 |
| **Tool Misuse** | 欺骗性提示操纵 agent 滥用集成工具 |
| **Intent Breaking** | 操纵 agent 计划重定向操作 |
| **Identity Spoofing** | 利用被入侵的认证伪装成合法 agent |
| **Code Attacks** | 利用 agent 执行代码的能力获得未授权访问 |

---

## 4. LLM 在安全测试中的局限性

| 局限性 | 描述 |
|--------|------|
| 高误报率 | Claude Code/Codex 误报率 50-100% |
| 非确定性分析 | 同一提示多次运行得到不同结果 |
| Context Rot | 并非所有上下文都同等有效 |

---

## 5. 实践练习

### 练习 1: 使用 SAST 工具
1. 安装 Semgrep
2. 扫描一个代码仓库
3. 分析扫描结果

### 练习 2: 理解 AI 安全
1. 尝试 prompt injection 攻击
2. 了解如何防御

---

## 讲座资料

### Lecture 11: AI Testing and Security
- [Slides (PDF)](../slides/week6-lecture1-ai-qa-sast-dast.pdf)
- **Guest Speaker**: Isaac Evans, CEO of Semgrep

---

## 阅读材料

1. **[Semgrep 文档](https://semgrep.dev/docs)**
2. **[OWASP Top 10](https://owasp.org/www-project-top-ten/)**

---

## 作业

**[Week 6 Assignment](https://github.com/mihail911/modern-software-dev-assignments/blob/master/week6/assignment.md)**

学习编写安全的 AI 代码，实施安全测试。

---

## 明天预告

Day 7 将探讨现代软件支持，学习 AI Code Review 的实践。

---

*学习时间建议: 10-12 小时*

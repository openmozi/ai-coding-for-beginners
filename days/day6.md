# 第 6 章：AI 测试与安全

## 课程概述

> "Software errors can dash user trust in a product/company and incur huge financial costs"

当 LLM 编写大部分代码时，需要广泛的护栏来防止错误。AI 时代的软件质量比以往任何时候都更重要。

### 学习目标
- 理解传统安全威胁和测试方法
- 掌握 SAST、DAST、SCA 等安全测试技术
- 了解 AI Agent 新型攻击向量
- 学习 LLM 在安全测试中的局限性

---

## 1. 传统威胁 landscape

### OWASP Top 10 威胁

| 威胁类型 | 描述 |
|----------|------|
| SQL Injections | SQL 注入攻击 |
| Cross-site scripting (XSS) | 跨站脚本攻击 |
| Broken authentication | 认证破损 |
| Insecure direct object references | 不安全的直接对象引用 |
| Security misconfigurations | 安全配置错误 |
| Sensitive data exposure | 敏感数据泄露 |

---

## 2. 漏洞检测技术

### SAST（静态应用安全测试）
- **类型**: White box testing（白盒测试）
- **分析**: 二进制文件和源代码
- **阶段**: 软件开发周期早期（成本最低）
- **技术**: 代码库模式匹配扫描
- **发现**: SQL 注入、命令注入、跨站脚本

### DAST（动态应用安全测试）
- **类型**: Black box testing（黑盒测试）
- **方法**: 模拟真实世界黑客行为发现漏洞
- **阶段**: 整个 SDLC，误报较少
- **技术**:
  - Input fuzzing（输入模糊测试）
  - Manipulating session tokens（会话令牌操作）
  - Configuration/header testing（配置/头测试）
  - Brute force rate-limit tests（暴力破解限速测试）

### SCA（软件组成分析）
- **分析**: 应用使用的开源软件包深度分析
- **方法**: 分析包管理器、基础设施即代码、pull 镜像
- **技术**: 扫描依赖漏洞

### 测试方法对比

| 方法 | 类型 | 阶段 | 优点 |
|------|------|------|------|
| SAST | White box | 早期 | 成本低，覆盖广 |
| DAST | Black box | 整个 SDLC | 误报少，发现运行时问题 |
| SCA | 依赖分析 | 构建时 | 检查第三方库漏洞 |

---

## 3. 发生了什么变化？

### Shift Left 安全
- "Shift left" 安全比以往任何时候都更容易获取
- 可以在工作流中引入 LLM 发现问题
- 自动化渗透测试

### LLM 在安全测试中的应用
- 自动化代码审查
- 漏洞检测
- 修复建议

---

## 4. AI Agent 新型攻击向量

| 攻击类型 | 描述 |
|----------|------|
| **Prompt Injection** | 隐藏或误导性指令使 AI 偏离预期行为 |
| **Tool Misuse** | 欺骗性提示操纵 agent 滥用集成工具 |
| **Intent Breaking** | 操纵 agent 计划重定向操作远离原始意图 |
| **Identity Spoofing** | 利用被入侵的认证伪装成合法 agent |
| **Code Attacks** | 利用 agent 执行代码的能力获得未授权访问执行环境 |

---

## 5. LLM 在安全测试中的局限性

| 局限性 | 描述 |
|--------|------|
| **高误报率** | Claude Code/Codex 误报率 50-100%，取决于漏洞类型 |
| **非确定性分析** | 同一提示多次运行得到不同结果，如何知道是否发现所有漏洞？ |
| **Context Rot** | 并非所有上下文都同等有效 |
| **Compaction** | 总结导致上下文压缩，信息丢失 |
| **基准不现实** | 现有基准往往不现实，难以评估 LLM |

### 与传统 SAST 比较
- AI SAST 误报率：50-100%（取决于漏洞）
- 传统 SAST 误报率：50%+

---

## 6. 开放性问题

| 问题 |
|------|
| 如何减少漏洞检测中的误报和幻觉？ |
| 如何验证 LLM 生成的补丁是安全的且没有引入回归？ |
| LLM 如何解释为什么标记漏洞或提出修复？ |
| 什么是衡量 LLM 应用安全性能的正确答案？ |
| LLM应该如何嵌入 CI/CD 而不产生过多噪音？ |
| 如果 AI 生成的补丁引入漏洞，谁负责？ |

---

## 7. 实践练习

### 练习 1: 使用 SAST 工具
1. 安装 Semgrep
2. 扫描一个代码仓库
3. 分析扫描结果

### 练习 2: 理解 AI 安全
1. 尝试 prompt injection 攻击
2. 了解如何防御

### 练习 3: 安全代码审查
使用 AI 工具进行安全代码审查

---

## 讲座资料

### Lecture 11: AI Testing and Security
- [Slides (PDF)](../slides/week6-lecture1-ai-qa-sast-dast.pdf)
- **Guest Speaker**: Isaac Evans, CEO of Semgrep
- **日期**: 10/31/25

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


# 第 7 章：现代软件支持

## 课程概述

> "Software code review is one of the highest leverage activities you can do to become a better engineer"

Code Review 是最高杠杆的活动。AI Code Review 比以往任何时候都更重要。

### 学习目标
- 理解 Code Review 的重要性
- 掌握 Code Review 的最佳实践
- 学习 AI Code Review 工具的使用
- 了解 AI Code Review 的局限性

---

## 1. Code Review 统计数据

| 指标 | 数据 |
|------|------|
| Code Review 错误检测率 | 55-60% |
| 无 Code Review 错误率 | 4.5 errors/100 lines |
| 有 Code Review 错误率 | 0.82 errors/100 lines |
| AT&T 案例 | 生产力提升 14%，缺陷减少 90% |
| 测试模式错误检测率 | 25-45% |

**来源**: Coding Horror

---

## 2. Code Review 要检查什么？

### 逻辑和正确性
- 代码逻辑是否正确？
- 是否有 bug？
- 边界情况是否处理？

### 可读性和可维护性
- 代码是否清晰易读？
- 命名是否合理？
- 函数是否过长？

### 性能
- 是否有性能问题？
- 算法是否最优？
- 是否有不必要的计算？

### 安全
- 是否有安全漏洞？
- 输入验证是否充分？
- 是否有敏感数据泄露风险？

### 最佳实践
- 是否遵循项目规范？
- 是否遵循语言/框架最佳实践？
- 是否有重复代码？

---

## 3. 好的 Code Review vs 差的 Review

### 差的 Review
> "This won't work"

### 好的 Review
> "I see your new method matches the existing style in this file, taking [X] parameters. Having that many parameters hurts readability and implies the function is doing too much. What do you think about refactoring this method and the existing ones in a later pull request to reduce how many parameters they take?"

**来源**: Blake Smith

---

## 4. AI Code Review 工具

### 现有工具

| 工具 | 描述 |
|------|------|
| **Graphite** | AI Code Review 平台，本课嘉宾 |
| **Greptile** | AI 代码审查服务 |
| **CodeRabbit** | AI 驱动的代码审查 |
| **Claude Code / Codex** | AI 辅助代码审查 |

---

## 5. AI Code Review 改变了什么？

| 方面 | 变化 |
|------|------|
| **效率** | 快速扫描大量代码，发现问题 |
| **一致性** | 应用相同的标准到所有代码 |
| **知识共享** | 传播团队最佳实践 |
| **降低认知负担** | 自动化常规检查 |
| **持续改进** | 系统随时间学习改进 |
| **整体理解** | 更全面理解代码库 |

**来源**: Greptile, Graphite

---

## 6. AI Code Review 的局限

### 局限

| 局限 | 描述 |
|------|------|
| **更多配置/设置** | 需要额外配置和学习 |
| **误报** | 需要持续训练系统学习 |
| **无法捕捉习语** | 还不一定能捕捉特定 repo 的习语和最佳实践 |
| **复杂逻辑** | 无法处理复杂业务逻辑和架构决策 |
| **安全变更需谨慎** | 安全变更必须格外小心 |
| **边缘情况** | 经常遗漏边缘情况 |

> **重要提醒**：Code Review with AI is more important than ever。
> 你拥有合并的代码，不能责怪 AI。AI 是助手，你才是最终负责人。

---

## 7. 实践练习

### 练习 1: 练习 Code Review
每天进行 Code Review 练习，养成习惯。

### 练习 2: 使用 AI 辅助 Review
使用 Graphite 或 Claude Code 辅助 Code Review。

### 练习 3: 改进 Review 质量
学习提供建设性的 Code Review 反馈。

---

## 讲座资料

### Lecture 13: AI Code Review
- [Slides (PDF)](../slides/week7-lecture1-code-review.pdf)
- **Guest Speaker**: Tomas Reimers, CPO of Graphite
- **日期**: 11/7/25

---

## 阅读材料

1. **[Code Reviews: Just Do It](https://blog.codinghorror.com/code-reviews-just-do-it/)**
2. **[How to Review Code Effectively](https://github.blog/developer-skills/github/how-to-review-code-effectively-a-github-staff-engineers-philosophy/)**

---

## 作业

**[Week 7 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week7)**

练习 Code Review，培养代码审查能力。

---

## 下一章

[下一章：Chapter 8](./chapter8.md)

---

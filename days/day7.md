# 第 7 章：现代软件支持

## 课程概述

> "Software code review is one of the highest leverage activities you can do to become a better engineer"

Code Review 是最高杠杆的活动。AI Code Review 比以往任何时候都更重要。

### 统计数据

| 指标 | 数据 |
|------|------|
| Code Review 错误检测率 | 55-60% |
| 无 Code Review 错误率 | 4.5 errors/100 lines |
| 有 Code Review 错误率 | 0.82 errors/100 lines |
| AT&T 案例 | 生产力提升 14%，缺陷减少 90% |

---

## 1. Code Review 要检查什么？

| 类别 | 描述 |
|------|------|
| **逻辑和正确性** | 代码逻辑是否正确？是否有 bug？ |
| **可读性和可维护性** | 代码是否清晰易读？命名是否合理？ |
| **性能** | 是否有性能问题？算法是否最优？ |
| **安全** | 是否有安全漏洞？输入验证是否充分？ |
| **最佳实践** | 是否遵循项目规范和最佳实践？ |

---

## 2. 好的 Code Review vs 差的 Review

**差的 Review**：
> "This won't work"

**好的 Review**：
> "I see your new method matches the existing style in this file, taking [X] parameters. Having that many parameters hurts readability and implies the function is doing too much. What do you think about refactoring this method...?"

---

## 3. AI Code Review 工具

| 工具 | 描述 |
|------|------|
| **Graphite** | AI Code Review 平台，本课嘉宾 |
| **Greptile** | AI 代码审查服务 |
| **CodeRabbit** | AI 驱动的代码审查 |

---

## 4. AI Code Review 改变了什么？

| 方面 | 变化 |
|------|------|
| **效率** | 快速扫描大量代码，发现问题 |
| **一致性** | 应用相同的标准到所有代码 |
| **知识共享** | 传播团队最佳实践 |
| **降低认知负担** | 自动化常规检查 |

---

## 5. AI Code Review 的局限

- 更多配置/设置
- 误报（需要持续学习）
- 无法捕捉特定 repo 的习语
- 无法处理复杂逻辑（需要人类）
- 安全变更需谨慎

> **重要提醒**：Code Review with AI is more important than ever。
> 你拥有合并的代码，不能责怪 AI。AI 是助手，你才是最终负责人。

---

## 6. 实践练习

### 练习 1: 练习 Code Review
每天进行 Code Review 练习，养成习惯。

### 练习 2: 使用 AI 辅助 Review
使用 Graphite 或 Claude Code 辅助 Code Review。

---

## 讲座资料

### Lecture 13: AI Code Review
- [Slides (PDF)](../slides/week7-lecture1-code-review.pdf)
- **Guest Speaker**: Tomas Reimers, CPO of Graphite

---

## 阅读材料

1. **[Code Reviews: Just Do It](https://blog.codinghorror.com/code-reviews-just-do-it/)**
2. **[How to Review Code Effectively](https://github.blog/developer-skills/github/how-to-review-code-effectively-a-github-staff-engineers-philosophy/)**

---

## 作业

**[Week 7 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week7)**

练习 Code Review，培养代码审查能力。

---

## 明天预告

Day 8 将探讨自动化 UI 和应用构建，学习 AI 如何改变前端开发。

---

*学习时间建议: 8-10 小时*

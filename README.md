# AI 编程入门教程

> 基于 Stanford University CS146S: The Modern Software Developer (Fall 2025)

**[English Version](README_EN.md)** | [学习检查清单](CHECKLIST.md) | [资源汇总](resources/README.md)

---

## 每日课程概览

| 天数 | 主题 | 讲座 | 幻灯片 | 学习资料 |
|------|------|------|--------|----------|
| [Day 1](days/day1.md) | 编程 LLM 和 AI 开发入门 | Lecture 1-2 | [PDF](/slides/week1-lecture1-introduction.pdf) [PDF](/slides/week1-lecture2-power-prompting.pdf) | [资料](days/day1.md) |
| [Day 2](days/day2.md) | 编程智能体的架构 | Lecture 3-4 | [PDF](/slides/week2-lecture1-coding-agent-scratch.pdf) [PDF](/slides/week2-lecture2-mcp-server.pdf) | [资料](days/day2.md) |
| [Day 3](days/day3.md) | AI 集成开发环境 | Lecture 5-6 | [PDF](/slides/week3-lecture1-ide-setup.pdf) [PDF](/slides/week3-lecture2-cognition.pdf) | [资料](days/day3.md) |
| [Day 4](days/day4.md) | 编程智能体模式 | Lecture 7-8 | [PDF](/slides/week4-lecture1-agent-manager.pdf) [PDF](/slides/week4-lecture2-claude-code.pdf) | [资料](days/day4.md) |
| [Day 5](days/day5.md) | 现代终端 | Lecture 9-10 | [PDF](/slides/week5-lecture1-ai-developer-product.pdf) | [资料](days/day5.md) |
| [Day 6](days/day6.md) | AI 测试与安全 | Lecture 11-12 | [PDF](/slides/week6-lecture1-ai-qa-sast-dast.pdf) | [资料](days/day6.md) |
| [Day 7](days/day7.md) | 现代软件支持 | Lecture 13-14 | [PDF](/slides/week7-lecture1-code-review.pdf) | [资料](days/day7.md) |
| [Day 8](days/day8.md) | 自动化 UI 和应用构建 | Lecture 15-16 | [PDF](/slides/week8-lecture1-end-to-end-apps.pdf) [PDF](/slides/week8-lecture2-vercel.pdf) | [资料](days/day8.md) |
| [Day 9](days/day9.md) | Agent 部署后运维 | Lecture 17-18 | [PDF](/slides/week9-lecture1-incident-response.pdf) | [资料](days/day9.md) |
| [Day 10](days/day10.md) | AI 软件工程的未来 | Lecture 19-20 | - | [资料](days/day10.md) |

---

## 课程简介

在大语言模型时代，软件开发正在经历一场革命性的变革。传统的软件开发生命周期正在被 AI 自动化所重塑。本课程将帮助你掌握现代 AI 编程工具，理解 AI 辅助开发的最佳实践，并为未来的软件工程职业做好准备。

### 课程信息

- **课程代码**: CS146S
- **学校**: Stanford University
- **学期**: Fall 2025
- **学分**: 3 units
- **官方网站**: https://themodernsoftware.dev

### 先修要求

- CS111 同等编程经验
- CS221/229 推荐（但非必需）

### 课程形式

- 每周讲座
- 实践编程环节
- 行业嘉宾演讲
- 期末项目展示

### 课程目标

- 掌握现代开发工具
- 理解 AI 辅助编程
- 学习自动化测试和部署
- 探索软件工程的新兴趋势

### 评分标准

| 组成部分 | 权重 |
|---------|------|
| 期末项目 | 80% |
| 每周作业 | 15% |
| 课堂参与 | 5% |

---

## 特色内容

### Anthropic 内部实践

本教程整合了 **How Anthropic Teams Use Claude Code** 阅读材料，来自 Anthropic 内部团队的实战经验：

| 团队 | Claude Code 应用场景 |
|------|---------------------|
| **Data Infrastructure** | Kubernetes 调试、数据工作流自动化、新人代码库导航 |
| **Product Development** | 产品功能开发、Bug 修复、重构 |
| **Security Engineering** | 安全代码审查、漏洞修复、威胁建模 |
| **Data Science** | 数据分析、可视化、实验分析 |
| **API Team** | API 文档生成、SDK 开发 |
| **Growth Marketing** | A/B 测试分析、营销自动化 |
| **Product Design** | 设计系统文档、原型迭代 |
| **RL Engineering** | 强化学习训练流程 |
| **Legal** | 合同分析、工作流程自动化 |

### 最佳实践要点

1. **详细的 Claude.md 文件** - 记录工作流、工具和期望
2. **使用 MCP 服务器** - 扩展 Claude Code 能力
3. **截图辅助** - 用截图展示期望的界面
4. **增量开发** - 一次实现一个步骤
5. **会话末文档** - 总结完成的工作，改进工作流

---

## 项目结构

```
ai-coding-for-beginners/
├── README.md                 # 本文件 - 课程概述
├── README_EN.md             # English version
├── CHECKLIST.md             # 学习检查清单
├── days/                    # 每日学习内容（中文）
├── days_en/                 # Daily tutorials (English)
├── notes/                   # 学习笔记（中文）
├── notes_en/                # Study notes (English)
├── slides/                  # 课程讲义 PDF
├── readings/                # 阅读材料
└── resources/               # 资源汇总
```

---

## 课程团队

- **Mihail Eric** - Instructor
- **Febie Lin** - TA
- **Brent Ju** - TA

---

## 资源链接

### 官方资源
- [课程官网](https://themodernsoftware.dev)
- [作业仓库](https://github.com/mihail911/modern-software-dev-assignments)

### 推荐工具
- Claude Code - Anthropic 的 AI 编程助手
- Warp - 现代终端
- Cursor - AI IDE
- GitHub Copilot - AI 代码补全

---

## 学习路径建议

1. **初学者路径**: 按顺序从 Day 1 开始学习
2. **进阶开发者**: 可以跳过 Day 1-2，直接从 Day 3 开始
3. **特定主题学习**: 根据兴趣选择特定天数深入学习

---

*本教程基于 Stanford CS146S 课程整理，仅供学习参考使用。*

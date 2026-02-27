# 第 9 章：Agent 部署后运维

## 课程概述

> "Monitoring software systems in production remains a mission-critical task"

Coding 只占工程时间的 30%，更难的 70% 是运行代码。

### 学习目标
- 理解传统 SRE 职责
- 掌握四个黄金监控信号
- 学习事件响应手册
- 了解 AI SRE 的特征和局限

---

## 1. 传统 SRE 职责

| 职责 | 描述 |
|------|------|
| **运营监控** | on-call、故障排除、基础设施管理和安全 |
| **事件解决** | 从多个不同来源和团队拼凑信息 |
| **维护手册** | 维护通常过时的故障排除手册 |
| **职业倦怠** | on-call 轮班导致 SRE 疲劳 |

### 现代化挑战
- 转向云原生架构
- 容器化工作负载和 Kubernetes
- 引入更多数据、依赖和系统复杂性

---

## 2. 四个黄金监控信号

| 信号 | 描述 |
|------|------|
| **Latency** | 延迟 |
| **Errors** | 错误 |
| **Traffic** | 流量（请求/秒） |
| **Saturation** | 饱和度 |

### 监控生产追踪
- 使用 traces 监控生产

---

## 3. 事件响应手册

### 场景
> 凌晨 3:12 你收到 PagerDuty 的通知，数据库查询出现 500 错误峰值。你该怎么办？

### 响应步骤

```
1. Acknowledge and assess（确认和评估）
2. Check DB + app（检查数据库和应用）
3. Identify recent changes（识别最近变更）
4. Localize blast radius（定位影响范围）
5. Execute mitigations（执行缓解措施）
6. Stabilize + monitor（稳定+监控）
7. Communicate（沟通）
8. Document（文档化）
```

### 关键指标

| 指标 | 描述 |
|------|------|
| **MTTR** | Mean-time-to-repair 平均修复时间 |
| **On-call 人数** | 事件需要多少工程师介入 |
| **SLA** | 客户报告的服务级别协议 |

---

## 4. 传统工具

### 现有 AI SRE 工具
- Resolve AI（本期嘉宾）
- DataDog Bits AI Agent
- Splunk Observability Assistant

---

## 5. AI SRE 的特征

> "AI SRE" = Agentic system across observability stack and clouds

| 特征 | 描述 |
|------|------|
| **动态知识图谱映射** | 实时理解系统组件关系 |
| **可观测性栈和云端的代理系统** | 跨平台智能监控 |
| **实时叙事** | 生成正在发生的情况的实时叙述 |
| **根因分析** | 找出可能根因及支持证据 |
| **修复建议** | 推荐明确的修复步骤 |
| **可解释性和可审计性** | 强调预测/推理的可解释性和可审计性 |

---

## 6. AI 改变了什么？

### 知识规模化
AI 承诺扩展组织和服务的知识：
- 信息不再局限于唯一了解未记录依赖、脆弱遗留服务和只有在高风险事件中才会表面化的怪癖的工程师

### 开发流程变化
- 自动化减少审查时间并尽早发现问题
- 开发者通过 AI 建议学习最佳实践
- AI 在所有代码审查中应用相同标准
- AI 处理常规检查，让人类专注于复杂逻辑
- AI 系统随时间推移和数据积累改进
- 现代 AI 代码审查工具提供更深入的情境分析和模式识别

---

## 7. AI SRE 的局限

| 局限 | 描述 |
|------|------|
| **事件复杂性** | 能解决的事件复杂度有限 |
| **生产栈异质性** | 现代生产栈的多样性 |
| **代码修复能力** | 根据检测到的内容修复实际代码的能力 |
| **监控园艺** | 好的根因分析需要好的监控维护 |
| **安全风险** | 可能成为新的攻击向量 |

### 最终目标
- 所有提供商从根因分析开始
- 最终目标是代码修复

---

## 8. 实践练习

### 练习 1: 学习监控基础
1. 了解四个黄金监控信号
2. 探索一个监控工具（如 DataDog）

### 练习 2: 事件响应演练
1. 模拟一个简单的事件
2. 按手册步骤响应

### 练习 3: 探索 AI SRE 工具
1. 了解 Resolve AI
2. 探索 DataDog Bits AI Agent

---

## 讲座资料

### Lecture 17: Incident response and DevOps
- [Slides (PDF)](../slides/week9-lecture1-incident-response.pdf)

### Lecture 18: Guest Speaker - Resolve AI
- **Guest Speaker**: Mayank Agarwal (CTO), Milind Ganjoo
- **日期**: 11/21/25

---

## 阅读材料

1. **[Introduction to Site Reliability Engineering](https://sre.google/sre-book/introduction/)**
2. **[Observability Basics](https://last9.io/blog/traces-spans-observability-basics/)**

---

## 作业

**[Week 9 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week9)**

实践 AI 辅助的事件响应流程。

---

## 下一章

[下一章：Chapter 10](./chapter10.md)

---

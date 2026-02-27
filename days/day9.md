# 第 9 章：Agent 部署后运维

## 课程概述

> "Monitoring software systems in production remains a mission-critical task"

Coding 只占工程时间的 30%，更难的 70% 是运行代码。

---

## 1. 传统 SRE 职责

| 职责 | 描述 |
|------|------|
| **运营监控** | on-call、故障排除、基础设施管理 |
| **事件解决** | 从多个不同来源和团队拼凑信息 |
| **维护手册** | 维护通常过时的故障排除手册 |
| **职业倦怠** | on-call 轮班导致 SRE 疲劳 |

---

## 2. 四个黄金监控信号

| 信号 | 描述 |
|------|------|
| **Latency** | 延迟 |
| **Errors** | 错误 |
| **Traffic** | 流量（请求/秒） |
| **Saturation** | 饱和度 |

---

## 3. 事件响应手册

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

## 4. AI SRE 的特征

> "AI SRE" = Agentic system across observability stack and clouds

| 特征 | 描述 |
|------|------|
| **动态知识图谱映射** | 实时理解系统组件关系 |
| **可观测性栈和云端的代理系统** | 跨平台智能监控 |
| **实时叙事** | 生成正在发生的情况的实时叙述 |
| **根因分析** | 找出可能根因及支持证据 |
| **修复建议** | 推荐明确的修复步骤 |

---

## 5. AI SRE 的局限

| 局限 | 描述 |
|------|------|
| 事件复杂性 | 能解决的事件复杂度有限 |
| 生产栈异质性 | 现代生产栈的多样性 |
| 监控园艺 | 好的根因分析需要好的监控维护 |

---

## 6. 实践练习

### 练习 1: 学习监控基础
1. 了解四个黄金监控信号
2. 探索一个监控工具（如 DataDog）

### 练习 2: 事件响应演练
1. 模拟一个简单的事件
2. 按手册步骤响应

---

## 讲座资料

### Lecture 17: Incident response and DevOps
- [Slides (PDF)](../slides/week9-lecture1-incident-response.pdf)

### Lecture 18: Guest Speaker - Resolve AI
- **Guest Speaker**: Mayank Agarwal (CTO), Milind Ganjoo

---

## 阅读材料

1. **[Introduction to Site Reliability Engineering](https://sre.google/sre-book/introduction/)**
2. **[Observability Basics](https://last9.io/blog/traces-spans-observability-basics/)**

---

## 作业

**[Week 9 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week9)**

实践 AI 辅助的事件响应流程。

---

## 明天预告

Day 10 将探讨 AI 软件工程的未来，讨论软件开发角色的演变和行业趋势。

---

*学习时间建议: 8-10 小时*

# Improving Instruction Hierarchy in Frontier LLMs

> 来源: https://openai.com/index/instruction-hierarchy-challenge/
> 论文: arXiv:2603.10521 (A Training Dataset to Improve Instruction Hierarchy on Frontier LLMs)
> 论文 PDF: https://cdn.openai.com/pdf/14e541fa-7e48-4d79-9cbf-61c3cde3e263/ih-challenge-paper.pdf
> 发布日期: 2026-03-10
> 类别: Safety - 指令安全与对抗鲁棒性

---

## 一、核心概述

OpenAI 发布了 **IH-Challenge（Instruction Hierarchy Challenge）** 训练数据集，通过大规模 **Reinforcement Learning（强化学习）** 微调，迫使前沿 LLM 严格遵循指令层级优先级，显著增强模型对 **Prompt Injection（提示注入）** 攻击的鲁棒性。核心思想是：许多 AI 安全失败的根本原因在于**模型执行了错误来源的指令**。

---

## 二、指令层级定义

IH-Challenge 建立了明确的四级指令优先级体系：

```
system ≻ developer ≻ user ≻ tool
```

- **System（系统级）**: 最高优先级，固定安全规则
- **Developer（开发者级）**: 通过 system message 设置的应用特定行为
- **User（用户级）**: 终端用户的请求
- **Tool（工具级）**: 来自外部工具调用的返回信息（最低优先级）

当不同级别的指令发生冲突时，模型必须**始终优先执行更高级别的可信指令**。

---

## 三、IH-Challenge 数据集设计

### 3.1 四种任务类型

| 任务类型 | 说明 |
|---------|------|
| **Single-Constraint（单约束）** | 测试模型遵循单一高优先级约束的能力 |
| **Multi-Constraint（多约束）** | 同时存在多个不同级别的约束，测试优先级判断 |
| **Input-Conditioned（输入条件）** | 根据输入内容动态决定是否遵循某指令 |
| **Anti-Overrefusal（反过度拒绝）** | 确保模型不因安全训练而变得过度保守，不应拒绝合法请求 |

### 3.2 设计原则

- 与 **OpenAI Model Spec**（2025-12-18 版本）的 Chain of Command 框架对齐
- 区分**指令遵循失败**（因任务复杂度导致）和**指令层级失败**（因优先级判断错误导致）
- 涵盖多种攻击向量，包括伪装、社工和嵌入式恶意指令

---

## 四、训练方法

- 采用**大规模强化学习（RL）微调**
- 在 **GPT-5 Mini** 基础上训练得到 **GPT-5 Mini-R**（R = Reinforced）
- RL 训练使模型学会在遭遇冲突指令时"思考"指令来源的可信度

---

## 五、核心结果

### 5.1 Prompt Injection 防御性能

| 评估指标 | GPT-5 Mini（基线） | GPT-5 Mini-R（RL训练后） | 提升 |
|---------|-------------------|------------------------|------|
| **Impersonation attacks（冒充攻击）** | 0.23 | **0.94** | +308% |
| **Automated attacks（自动化攻击）** | 0.73 | **0.97** | +33% |
| **Human red-teaming（人工红队测试）** | 0.90 | **0.90** | 持平 |

### 5.2 评估基准

- **CyberSecEval 2**: 学术基准，评估网络安全相关的指令遵循能力
- **OpenAI 内部 Prompt Injection Benchmark**: 包含针对 ChatGPT Atlas 测试过的攻击样本

### 5.3 关键发现

- RL 训练在**冒充攻击**场景下提升最为显著（从 0.23 到 0.94）
- 对**自动化攻击**也有显著改善
- 人工红队测试得分保持不变，说明高级人类攻击者仍然具有挑战性
- **反过度拒绝**任务确保安全增强不以牺牲可用性为代价

---

## 六、为什么指令层级是基础安全要求

### 6.1 Agent 时代的必要性

随着 AI Agent 变得更加自主（调用工具、读取不可信文档、执行代码），它们需要可靠地**区分合法指令和操纵性指令**：
- 读取的网页可能包含隐藏的恶意指令
- 工具返回的数据可能被注入对抗性内容
- 用户请求可能伪装为系统级指令

### 6.2 与安全失败的根本关联

OpenAI 指出，大多数 AI 安全失败（包括 prompt injection）共享一个**共同根因**：模型遵循了**错误的指令**。强化指令层级是解决这一类问题的**系统性方案**。

---

## 七、关联分析

### 与 Model Spec / Chain of Command 的关联

IH-Challenge 直接实现了 **Model Spec**（2026-03-25 博客）中定义的 Chain of Command 框架。Model Spec 定义了理论层级（Root > System/Developer > User），IH-Challenge 将其转化为可训练的数据集和可量化的评估指标。两者是**规范与实现**的关系。

### 与 Detecting Scheming 的关联

**Detecting and Reducing Scheming in AI Models** 中的 Anti-Scheming 训练通过 Deliberative Alignment 减少欺骗行为。IH-Challenge 从**指令优先级**角度、Scheming 研究从**模型意图**角度，共同解决"如何确保模型按预期行为运作"的问题。两者是同一安全问题的**不同维度**。

### 与 CoT Control / Monitorability 的关联

**CoT Controllability** 研究表明推理模型难以控制自身的思维链，这使得思维链成为可靠的**安全监控信号**。当 IH-Challenge 训练后的模型面对冲突指令时，其思维链中的推理过程可被用于验证模型是否正确执行了指令层级判断。

### 与 GPT-5.3-Codex 的关联

GPT-5.3-Codex 作为首个网络安全"高"能力模型，其 **Safety Reasoner** 需要强大的指令层级遵循能力来正确处理高风险双用途请求。IH-Challenge 的训练方法为 Codex 系列模型的安全推理提供了**基础能力支撑**。

### 与 GPT-5.4 Thinking System Card 的关联

GPT-5.4 Thinking 的安全评估中，指令层级遵循是核心评估维度之一。IH-Challenge 的成果直接应用于最新旗舰模型的安全训练流程。

---

## 八、核心洞察

1. **统一根因分析**: 将 prompt injection、指令冲突等看似不同的安全问题归结为"模型遵循了错误指令"这一统一根因，是安全研究方法论的重要突破
2. **RL 是指令层级的有效训练手段**: 强化学习在冒充攻击防御上实现了 4 倍提升（0.23→0.94），证明了 RL 在安全训练中的潜力
3. **人类攻击者仍是瓶颈**: 人工红队测试得分未变（0.90），说明高级社工攻击仍然是当前防御体系的薄弱环节
4. **Anti-Overrefusal 是关键创新**: 在增强安全的同时防止过度拒绝，体现了"安全不应牺牲可用性"的设计哲学
5. **Agent 安全的基础设施**: 随着 AI Agent 生态扩展，指令层级将成为类似"操作系统权限管理"的基础安全设施

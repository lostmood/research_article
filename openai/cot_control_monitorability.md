# Reasoning Models Struggle to Control Their Chains of Thought

> 来源: https://openai.com/index/reasoning-models-cot-control/
> 论文: https://arxiv.org/abs/2603.05706
> 代码: https://github.com/YuehHanChen/CoTControl
> 发布日期: 2026-03-05
> 类别: Research - AI 安全 / 可监控性

---

## 一、核心概述

本文提出并系统性地测量了 **"CoT Controllability"（思维链可控性）**——即推理模型（reasoning model）在解决问题时，能否刻意抑制、修改或重塑其思维链（Chain of Thought）中表达的推理内容。

核心发现：**推理模型难以完美控制自身思维链**。这对 AI 安全而言是积极信号——意味着基于 CoT 的监控（CoT monitoring）仍然是可靠的安全层，因为模型很难通过操纵思维链来逃避监控。

研究团队来自 NYU 和 OpenAI，与 GPT-5.4 同日发布，作为其安全评估的理论基础。

---

## 二、关键技术细节

### 2.1 问题定义

- **CoT Monitoring（思维链监控）**：通过审查模型的推理过程来检测潜在的不安全行为，是当前 AI 安全的关键防线
- **CoT Controllability（思维链可控性）**：模型在保持正确答案的同时，能否按要求控制其 CoT 内容（如"回答遗传学问题但不使用'chromosome'一词"）
- **核心假设**：如果模型能轻松控制 CoT，则可能隐藏真实推理意图，CoT 监控将失效

### 2.2 CoT-Control 评估套件

构建了包含 **13,000+ 任务**的评估框架，覆盖 **24 个环境**：

| 数据来源 | 任务类型 |
|----------|----------|
| GPQA | 科学推理 |
| MMLU-Pro | 多领域知识 |
| HLE（Humanity's Last Exam） | 极高难度推理 |
| BFCL | 函数调用 |
| SWE-Bench Verified | 软件工程 |

任务设计：模型必须**在遵守 CoT 约束的同时正确解决问题**。例如，正确回答遗传学问题但思维链中不能出现特定关键词。

### 2.3 跨 13 个前沿模型的评估结果

| 模型 | CoT 可控性 | 输出可控性 | 差异 |
|------|-----------|-----------|------|
| Claude 3.7 Sonnet | 36.1% | 59.5% | -23.4% |
| Claude Sonnet 4 | 19.0% | 56.1% | -37.1% |
| Claude Sonnet 4.5 | 2.7% | 61.9% | -59.2% |
| GPT-5 | 2.6% | 66.3% | -63.7% |
| o3 | 2.8% | 62.4% | -59.6% |
| o4-mini | **0.1%** | 48.6% | -48.5% |
| DeepSeek R1 | 0.7% | 53.8% | -53.1% |

**关键发现**：所有模型的 **CoT 可控性远低于输出可控性**，差距通常在 20-60 个百分点。

### 2.4 影响因素分析

四个关键变量如何影响 CoT 可控性：

1. **模型容量（Model Capacity）**：更大的模型 → CoT 可控性略高
2. **推理训练（Reasoning Training）**：经过强化学习推理训练的模型 → CoT 可控性**降低**（跨 4 个模型家族验证）
3. **推理计算量（Test-time Compute）**：更多推理计算 → CoT 可控性**降低**
4. **任务难度（Task Difficulty）**：更简单的任务 → CoT 可控性略高（因为模型可以进行隐式推理，不依赖显式 CoT）

### 2.5 对抗性测试

- **告知模型正在被监控**：仅产生边际改善
- **对抗性提示优化（Adversarial Prompt Optimization）**：未能有意义地增强 CoT 可控性
- 表明 CoT 不可控性是**结构性特征**，而非简单的提示工程问题

---

## 三、安全意义

### 3.1 "谨慎乐观"的结论

作者的核心立场是 **"cautiously optimistic"（谨慎乐观）**：

> "CoT controllability is currently unlikely to be a failure mode of CoT monitorability."
> （CoT 可控性目前不太可能成为 CoT 可监控性的失败模式。）

### 3.2 重要警告

低可控性 **≠** 保证高可监控性。可监控性仍可能因以下原因退化：

- **直接优化压力**：如果训练过程直接优化 CoT 内容，可能改变可控性特征
- **机制不明**：当前 CoT 不可控性的底层机制尚未被完全理解
- **未来模型可能不同**：随着模型架构和训练方法演进，CoT 可控性特征可能变化

### 3.3 OpenAI 的承诺

- 未来系统卡片中同时报告 **CoT controllability** 和 **CoT monitorability**
- **不对前沿推理模型的 CoT 施加直接优化压力**
- 已在 GPT-5.4 Thinking 系统卡片中首次执行此承诺

---

## 四、关联分析

### 与 GPT-5.4 / GPT-5.4 Thinking 的关联

本研究是 GPT-5.4 发布的配套安全研究，直接服务于 [GPT-5.4 Thinking 系统卡片](gpt_5_4_thinking_system_card.md)的安全评估。GPT-5.4 Thinking 是首个在系统卡片中报告 CoT 可控性指标的模型。

### 与 Detecting Scheming 的关联

本研究与 [Detecting & Reducing Scheming](detecting_reducing_scheming_ai.md) 形成互补安全研究矩阵：
- **CoT Control**：模型能否在 CoT 中隐藏推理？→ 当前很难
- **Scheming Detection**：模型是否会产生欺骗性策略行为？→ 需要主动检测

两者共同构成了 OpenAI 对"模型对齐透明度"问题的研究闭环。

### 与 Model Spec 的关联

Model Spec（2026-03-25）定义了模型应遵循的行为规范。CoT 可控性研究验证了 Model Spec 在推理层面的可执行性——如果模型无法控制 CoT，则更难违反行为规范而不被检测到。

### 与行业趋势的关联

随着 Anthropic（Claude）、Google（Gemini）等厂商也在部署推理模型，CoT 监控的有效性是全行业共同关注的安全议题。本文的开源评估套件为跨厂商的可比评估奠定了基础。

---

## 五、核心洞察

1. **CoT 不可控性是"意外的安全礼物"**：推理训练带来的副作用——模型越擅长推理，越难操纵自身推理过程——恰好为安全监控提供了天然屏障
2. **输出可控性 vs CoT 可控性的巨大鸿沟**：模型可以轻松控制"说什么"，但很难控制"怎么想"。这一发现对理解 AI 系统的"内部透明度"具有深远意义
3. **安全属性的脆弱性**：作者明确警告这种安全属性可能随未来训练方法变化而消失，强调需要持续监测而非一劳永逸
4. **开源评估推动行业标准**：CoT-Control 评估套件的开源（GitHub）为建立行业级的推理透明度评估标准迈出了重要一步
5. **推理训练是双刃剑的积极面**：强化学习推理训练虽然提升了能力，但同时降低了 CoT 可控性，这是一个罕见的"能力提升与安全改善同向"的案例

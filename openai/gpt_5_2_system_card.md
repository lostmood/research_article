# GPT-5.2 System Card

> 来源: [OpenAI Blog](https://openai.com/index/gpt-5-2-system-card/) | [Deployment Safety Hub](https://deploymentsafety.openai.com/gpt-5-2)
> 发布日期: 2025-12-11
> 类别: Safety / System Card / Model Evaluation

---

## 核心概述

OpenAI 发布了 **GPT-5.2 安全系统卡片（System Card）**，作为 GPT-5 System Card 的更新版本。GPT-5.2 是 GPT-5 系列的最新旗舰模型，带来了 **推理（Reasoning）、工具使用（Tool Use）和长上下文处理（Long Context）** 方面的显著改进。模型提供三个层级：**Instant（快速）、Thinking（深度推理）和 Pro（最大计算）**，配备 **400K token 上下文窗口** 和 **128K 输出**。System Card 涵盖了全面的安全评估，包括越狱鲁棒性、提示注入防护、视觉安全、幻觉率、欺骗感知以及 Preparedness Framework 下的网络安全和生物安全评估。

---

## 关键技术细节

### 模型规格

| 参数 | 值 |
|------|------|
| **Model Family** | GPT-5.2 |
| **Context Window** | **400K tokens** |
| **Output Length** | **128K tokens** |
| **Knowledge Cutoff** | 2025 年 8 月 |
| **发布日期** | 2025 年 12 月 11 日 |
| **模型层级** | Instant / Thinking / Pro |

### 三个模型层级

| 层级 | 定位 | 特点 |
|------|------|------|
| **Instant** | 快速响应 | 低延迟，适用于日常交互 |
| **Thinking** | 深度推理 | 更强的推理能力，适用于复杂问题 |
| **Pro** | 最大计算 | 最高质量输出，投入最大计算资源 |

### 基准评估成绩

| 基准测试 | 成绩 |
|----------|------|
| **GPQA Diamond** | **93.2%** |
| **AIME** | **100%** |
| **GDPval** | **70.9%** |
| **ARC-AGI** | 首个突破 90% 的模型 |

### 安全评估

#### 越狱与提示注入（Jailbreak & Prompt Injection）

- **越狱鲁棒性**：相比 GPT-5/5.1 显著改进
- **提示注入防护**：更强的防御能力
- 推理能力帮助模型更可靠地遵循特定指南和安全策略

#### 视觉安全（Vision Safety）

- 在视觉相关安全基准上表现改进

#### 幻觉（Hallucination）

- 幻觉率低于前代模型

#### 欺骗感知（Deception Awareness）

- **GPT-5.2-Thinking** 可能表现出 **更高的被评估感知（Awareness of Being Evaluated）**
- 但欺骗率与同类模型总体相当
- 脚手架（Scaffolding）未显著放大欺骗行为

### Preparedness Framework 评估

#### 网络安全（Cybersecurity）

- 评估了 **真实世界漏洞识别能力**（pass@1 指标）
- 在 CTF 挑战中表现优异
- 实施了专项安全控制以平衡部署与防御需求

#### 生物安全（Biosafety）

- 评估了 **真实世界实验错误识别能力**（湿实验室故障排除）
- 在生物协议的错误识别方面进行了专项测试

#### ML 工程（ML Engineering）

- 在 **MLE-bench** 上评估了 ML 工程智能体能力（Kaggle 挑战）

### 长上下文与上下文压缩

- **400K token 上下文窗口** 支持超长文档和多轮对话
- **Context Compaction（上下文压缩）**：当接近上下文限制时，自动总结会话历史，支持多小时连续工作会话

---

## 关联分析

| 关联主题 | 说明 |
|----------|------|
| **Preparedness Framework** | OpenAI 评估前沿模型风险的核心框架 |
| **Reasoning（推理）** | GPT-5.2 的推理能力提升是安全改进的基础 |
| **Long Context（长上下文）** | 400K 上下文窗口带来新的安全挑战和机遇 |
| **Agentic Capabilities（智能体能力）** | 工具使用和多步任务执行的安全评估 |

### 与其他 OpenAI 产品/文档的关系

- **GPT-5.2-Codex System Card Addendum (2025-12-18)** — 编码专项安全补充
- **GPT-5.3-Codex System Card (2026-02-05)** — 后续 Codex 版本的安全评估
- **GPT-5.4 (introducing_gpt_5_4.md)** — 下一代旗舰模型
- **GPT-5.1-Codex-Max (introducing_gpt_5_1_codex_max.md)** — 前代 Codex 最大规格模型
- **safe-completions (2025-08)** — 安全补全机制
- **Prism (introducing_prism_latex.md)** — 基于 GPT-5.2 的科研写作工具
- **In-House Data Agent (in_house_data_agent.md)** — 基于 GPT-5.2 的内部数据智能体

### 竞争格局

| 模型 | 优势领域 |
|------|----------|
| **GPT-5.2** | 专业知识工作编排（Professional Knowledge-Work Orchestration） |
| **Google Gemini 3.0** | 多模态/图像生成 |
| **Anthropic Claude 4.5** | 透明推理（Transparent Reasoning） |

---

## 核心洞察

1. **推理能力驱动安全提升**：GPT-5.2 的安全改进很大程度上源于推理能力的提升——模型能更可靠地理解和遵循安全策略，而非仅依赖训练时的对齐。这是"能力即安全"理念的体现。

2. **欺骗感知的微妙信号**：GPT-5.2-Thinking 表现出更高的"被评估感知"，虽然欺骗率未显著增加，但这个信号值得持续关注——随着模型能力增强，欺骗检测和防护将变得更加重要。

3. **400K 上下文窗口的安全边界**：超长上下文既是能力飞跃，也带来新的安全挑战。上下文压缩技术在保持会话连贯性的同时，也需要确保安全策略在压缩后仍然有效。

4. **多领域 Preparedness 评估的深化**：从网络安全、生物安全到 ML 工程，GPT-5.2 的安全评估覆盖了更多真实世界场景，反映了 OpenAI 对前沿模型风险评估的日益系统化。

5. **三层级模型架构的安全含义**：Instant/Thinking/Pro 三个层级意味着不同的能力-安全权衡。Pro 层级的最大计算投入可能带来更强的推理和更好的安全遵从，但也需要更严格的防护措施。

6. **首个突破 ARC-AGI 90% 的模型**：这一里程碑标志着 GPT-5.2 在通用推理能力上的显著进步，也暗示了未来模型可能更快接近甚至突破"高"风险阈值的趋势。

# Introducing GPT-5.4 Mini and Nano — 面向子代理时代的小型模型

> 来源: https://openai.com/index/introducing-gpt-5-4-mini-and-nano/
> 发布日期: 2026-03-17
> 类别: Research - 模型发布

---

## 一、核心概述

GPT-5.4 mini 和 nano 是 OpenAI 于 2026 年 3 月 17 日发布的两款小型高效模型，专为 **"the subagent era"**（子代理时代）设计。核心理念是：在多代理架构（multi-agent architecture）中，不同复杂度的任务应由不同规模的模型处理，实现成本与性能的最优平衡。

---

## 二、GPT-5.4 Mini

### 关键特性
- **速度**: 比 GPT-5 mini **快 2 倍以上**
- **编码能力**: 达到 GPT-5.4 标准版 **94% 的编码性能**
- **多模态**: 支持文本和图像输入
- **工具使用**: 支持工具调用、函数调用、网络搜索和文件搜索
- **计算机使用**: OSWorld 基准 **72.1%**
- **上下文窗口**: 1,050K tokens

### 基准表现
| 基准 | GPT-5.4 Mini | GPT-5.4 标准 |
|------|-------------|-------------|
| SWE-Bench Pro | 53.4-54.4% | 57.7% |
| OSWorld | 72.1% | 75.0% |
| 编码性能比 | 94% | 100% |

### 定价
- **输入**: $0.75 / 1M tokens
- **输出**: $4.50 / 1M tokens
- 使用仅为 GPT-5.4 的 **30% 配额**

### 可用性
- ChatGPT（Free 和 Go 套餐的默认模型）
- Codex
- OpenAI API
- Microsoft Foundry

---

## 三、GPT-5.4 Nano

### 关键特性
- **超低延迟**: 针对轻量级任务优化
- **高吞吐量**: 约 **182.3 tokens/秒**
- **首词延迟（TTFT）**: 2.49 秒
- **文本优先设计**: 主要面向文本任务
- **上下文窗口**: 400K tokens

### 基准表现
| 基准 | GPT-5.4 Nano |
|------|-------------|
| SWE-Bench Pro | 52.39% |
| TerminalBench 2.0 | 46.30% |

### 定价
- **输入**: $0.20 / 1M tokens
- **输出**: $1.25 / 1M tokens

### 可用性
- OpenAI API 限定
- Microsoft Foundry

---

## 四、Mini vs Nano 对比

| 维度 | Mini | Nano |
|------|------|------|
| **目标用途** | 复杂快速任务 | 轻量级、成本敏感任务 |
| **最佳场景** | 实时编码、多模态推理、计算机使用 | 分类、数据提取、高容量部署 |
| **推理能力** | 强大 | 基础 |
| **编码能力** | SWE-Bench 54.4% | SWE-Bench 52.39% |
| **延迟** | 低 | 超低 |
| **成本** | 中等 | 极低 |

---

## 五、子代理时代（Subagent Era）的多代理架构

### 推荐架构分层

```
┌─────────────────────────────────┐
│  GPT-5.4 Standard / Thinking   │  ← 规划与判断层
│  (Planning & Judgment)          │
├─────────────────────────────────┤
│  GPT-5.4 Mini                  │  ← 执行层
│  (Complex Subtasks)             │
│  - 代码库搜索与文件审查          │
│  - 并行复杂子任务               │
│  - 工具选择与函数调用            │
│  - 计算机使用任务               │
├─────────────────────────────────┤
│  GPT-5.4 Nano                  │  ← 微任务层
│  (Micro Tasks)                  │
│  - 分类与实体提取               │
│  - 高容量请求路由               │
│  - 实时聊天                    │
│  - 轻量级自动化                │
└─────────────────────────────────┘
```

### 设计哲学

> "Built for the subagent era" — 为子代理时代而生

核心思想是**分层模型分配**（tiered model allocation）：
- **Nano** 处理简单、高频任务（classification, extraction, routing）
- **Mini** 处理需要推理但不需要最强能力的任务（coding, multimodal reasoning）
- **Standard/Thinking** 处理需要深度思考和判断的任务（planning, complex reasoning）

---

## 六、关联分析

### 与 GPT-5.4 发布的协同

GPT-5.4 mini 和 nano 在 GPT-5.4 标准版发布 12 天后推出，构成了完整的**模型梯队**。这种"旗舰 + 精简版"的发布策略呼应了 GPT-5.1（Instant + Thinking）和 GPT-5.2（Instant + Thinking + Pro）的模式，但 mini/nano 的定位更明确地指向了多代理系统。

### 与 Codex Agent 生态的关联

在 Codex 的智能体编码引擎中，Mini 使用仅 30% 的配额，使得 Codex 可以将低推理强度的工作委托给 mini 子代理，显著降低成本。这与 OpenAI 此前发布的 Codex 智能体（运行在隔离微型虚拟机中）的架构理念一致。

### 与行业趋势的关联

"子代理时代"概念反映了 AI 系统从"单一大模型"向"多模型协作"的架构演进：
- **Anthropic**: Claude Agent Teams（共享任务列表和通信）
- **OpenAI**: Codex 平行智能体 + Mini/Nano 子代理
- 两种路线都在探索如何让多个 AI 代理高效协作

### 与 ChatGPT Agent 的关联

GPT-5.4 mini 成为 ChatGPT Free 和 Go 用户的默认模型，标志着高性能 AI 能力的"民主化"。此前的 ChatGPT Agent（2025-07）引入了智能体模式，而 mini/nano 为这种智能体模式提供了更经济的计算基础。

---

## 七、核心洞察

1. **模型经济学新范式**: Mini/Nano 不仅是"更小的模型"，而是多代理架构中的**功能性角色**
2. **速度与成本的帕累托最优**: 94% 的性能 + 30% 的成本 = 子代理场景下的最优选择
3. **Nano 的战略定位**: 作为最小模型，Nano 可能成为边缘计算和嵌入式 AI 的关键角色
4. **统一与分化的辩证**: GPT-5.4 追求统一（编码+推理+计算机使用），而 mini/nano 追求分化（不同任务用不同模型），两者共同构成完整的生态策略

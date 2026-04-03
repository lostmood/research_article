# GPT-5.3 Instant System Card

> 来源: https://openai.com/index/gpt-5-3-instant-system-card/
> 部署安全页: https://deploymentsafety.openai.com/gpt-5-3-instant
> 发布日期: 2026-03-02
> 类别: Safety - 系统卡片（System Card）

---

## 一、核心概述

GPT-5.3 Instant 是 OpenAI GPT-5 系列的聊天优化模型（chat-oriented model），于 2026 年 2 月 26 日完成评估版本，**3 月 3 日**正式在 ChatGPT 和 API 中上线（API 模型名：`gpt-5.3-chat-latest`）。

定位：**速度更快、减少过度拒绝、改善上下文管理和网页搜索集成的对话模型**。核心改进是在保持安全性的前提下，解决 GPT-5.2 Instant 用户反馈的"过度谨慎"和"说教式"（preachy）回复问题。

---

## 二、关键技术细节

### 2.1 性能定位

GPT-5.3 Instant 在 OpenAI 内部评估体系中的定位：

| 维度 | 评估结果 |
|------|----------|
| 禁止内容评估 | 平均表现 **高于 GPT-5.1 Instant**，**低于 GPT-5.2 Instant** |
| 幻觉率（使用网页搜索） | 相比前代降低 **26.8%** |
| 幻觉率（仅内部知识） | 相比前代降低 **19.7%** |
| HealthBench | 54.1%（对比 GPT-5.2 Instant: -1.3%） |

### 2.2 核心改进

**速度与响应质量**：
- 更快的响应速度
- 更丰富、更好的上下文化回答（richer, better-contextualized answers）

**减少过度拒绝（Fewer Refusals）**：
- 直接回应了用户反馈：GPT-5.2 Instant 在敏感话题上过于谨慎
- 减少"说教式"（preachy）和"过度回避"（overly cautious）回复
- 不再过度"道德说教"（moralize），更加直接地回答问题

**幻觉控制**：
- 网页搜索场景下幻觉率降低 26.8% 是显著改进
- 纯内部知识场景下也降低 19.7%

### 2.3 安全评估

**安全回归（Safety Regressions）**：

系统卡片明确指出 GPT-5.3 Instant 在部分安全评估中出现回归：
- **性内容相关评估**：相对 GPT-5.2 Instant 有所退步
- **自残相关评估**：相对 GPT-5.2 Instant 有所退步
- 整体安全评分在 GPT-5.1 Instant 和 GPT-5.2 Instant 之间

**安全缓解方法**：
- 安全缓解方法与 GPT-5.2 Instant 系统卡片中描述的基本一致
- 系统级防护措施（system-level safeguards）维持运行

### 2.4 网页搜索集成

GPT-5.3 Instant 的网页搜索集成是重要改进方向：
- 集成搜索能力显著降低幻觉率
- 提供更好的上下文感知回答
- 搜索结果与模型回答的融合更加自然

---

## 三、模型生命周期

| 事件 | 日期 |
|------|------|
| 评估版本完成 | 2026-02-26 |
| 正式上线（ChatGPT + API） | 2026-03-03 |
| GPT-5.2 Instant 日落 | 2026-06-03 |
| API 模型名 | `gpt-5.3-chat-latest` |

---

## 四、关联分析

### 与 GPT-5.2 Instant 的对比

GPT-5.3 Instant 是对 GPT-5.2 Instant 的迭代优化，核心权衡是：

| 维度 | GPT-5.3 vs GPT-5.2 |
|------|---------------------|
| 拒绝率 | 更低（减少过度拒绝） |
| 幻觉率 | 更低（-26.8% / -19.7%） |
| 响应速度 | 更快 |
| 部分安全评估 | 有所回归 |
| HealthBench | 略低（-1.3%） |

这体现了**可用性与安全性之间的经典张力**——减少过度拒绝必然意味着在某些边界情况下安全防护的放松。

### 与 GPT-5.3-Codex 的关联

GPT-5.3-Codex（2026-02-05）是同系列的编码专用模型，获得了"高"网络安全风险评级。GPT-5.3 Instant 作为聊天模型，安全风险面不同但共享同一代模型基础。

### 与 GPT-5.4 的关联

GPT-5.3 Instant 定位为聊天导向模型，而 [GPT-5.4](introducing_gpt_5_4.md) 定位为专业工作模型。在 GPT-5.4 发布后，GPT-5.3 Instant 主要服务于日常对话场景，两者形成互补。GPT-5.4 将 GPT-5.3-Codex 的编码能力完全整合，标志着从"专用模型"向"统一模型"的转型。

### 与 Model Spec / Instruction Hierarchy 的关联

GPT-5.3 Instant 的"减少过度拒绝"策略与后续发布的 Instruction Hierarchy（2026-03-10）和 Model Spec（2026-03-25）形成呼应——这些框架试图更精细地定义模型应何时拒绝、何时配合，避免一刀切的过度拒绝。

### 与 Safe-Completions 的关联

GPT-5.3 Instant 延续了 GPT-5 引入的 safe-completions 安全方法——从硬拒绝转向以输出为中心的安全训练，这正是"减少过度拒绝"策略的技术基础。

---

## 五、核心洞察

1. **"减少拒绝"是用户驱动的产品决策**：OpenAI 直接回应了用户对 GPT-5.2 Instant "过度谨慎"的反馈，表明安全策略正在从"最大化安全"向"最优化安全-可用性平衡"转变
2. **安全回归是有意的权衡**：在性内容和自残评估上的回归不是意外，而是减少过度拒绝策略的预期代价。OpenAI 选择透明披露这一权衡
3. **幻觉控制取得实质进展**：网页搜索场景下 26.8% 的幻觉率降低是显著的工程成就，表明搜索增强生成（Search-Augmented Generation）路线的有效性
4. **Instant 系列定位于"日常对话"**：与 GPT-5.4 的"专业工作"定位形成分层，OpenAI 正在构建覆盖不同场景的模型矩阵
5. **系统卡片的坦诚度在提升**：明确披露安全回归区域而非只突出改进，反映了 OpenAI 在安全透明度方面的进步

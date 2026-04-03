# GPT-5.4 Thinking System Card

> 来源: https://deploymentsafety.openai.com/gpt-5-4-thinking
> 发布日期: 2026-03-05
> 类别: Safety - 系统卡片（System Card）

---

## 一、核心概述

GPT-5.4 Thinking 是 GPT-5 系列最新的推理模型（reasoning model），也是 GPT-5.4 的深度推理变体。本系统卡片详细记录了该模型的安全评估、风险分类和缓解措施。

核心定位：**针对专业工作（professional work）、编码（coding）、计算机使用（computer use）和工具搜索（tool search）优化的前沿推理模型**，支持高达 **1M token 上下文窗口**。

关键安全里程碑：GPT-5.4 Thinking 是 OpenAI **首个在 Preparedness Framework 下以"高"网络安全风险评级（high cyber risk rating）发布的通用模型**。

---

## 二、关键技术细节

### 2.1 能力概览

| 能力 | 详情 |
|------|------|
| 上下文窗口 | 1M tokens（实验性） |
| 原生计算机使用 | 首个具备原生 Computer Use 的通用模型 |
| Tool Search | 新 API 能力，token 使用减少 47% |
| 全分辨率视觉处理 | Full-resolution vision processing |
| 事实准确性 | 单个声明虚假概率降低 33%，完整回复错误概率降低 18% |

### 2.2 基准性能

| 基准 | GPT-5.4 | 对比 GPT-5.2 | 说明 |
|------|---------|-------------|------|
| GDPval | 83.0% | 70.9% | 44 职业专业工作匹配/超越专业人士 |
| OSWorld-Verified | 75.0% | - | 首个超越人类表现的计算机使用基准 |
| Toolathlon | 54.6% | 46.3% | 多步工具使用 |

### 2.3 Preparedness Framework 评估

GPT-5.4 Thinking 在 OpenAI 的 **Preparedness Framework**（安全准备框架）下接受了全面评估：

- **网络安全风险等级：高（High）** — 这是 OpenAI 首次以该等级发布通用模型，此前仅 GPT-5.3-Codex 获得过同等评级
- **CBRN 评估**：涵盖化学、生物、放射性、核（Chemical, Biological, Radiological, Nuclear）领域的危险知识提升（uplift）评估
- **模型可监控性**：GPT-5.4 Thinking 在部分类别中显示出**低于 GPT-5 的聚合可监控性**（lower aggregate monitorability），OpenAI 认为这部分反映了评估方法论的局限

### 2.4 安全基准评分

**标准禁止内容评估（Disallowed Content Evaluation）**：

| 类别 | gpt-5-thinking-mini | gpt-5-thinking-nano | o4-mini |
|------|---------------------|---------------------|---------|
| 仇恨言论（Hate） | 0.996 | 0.987 | 0.983 |
| 非法/非暴力 | 1.000 | 0.991 | 0.991 |
| 非法/暴力 | 1.000 | 1.000 | 1.000 |
| 涉未成年人性内容 | 0.990 | 0.990 | 1.000 |
| 自残 | 0.989 | 0.989 | 1.000 |

**StrongReject 基准**：

| 类别 | gpt-5-thinking-mini | o4-mini |
|------|---------------------|---------|
| 非法/非暴力提示 | 0.994 | 0.968 |
| 暴力提示 | 0.996 | 0.972 |
| 滥用/虚假信息/仇恨 | 0.973 | 0.973 |
| 性内容 | 0.994 | 0.970 |

（数值越高 = 越好地拒绝禁止内容）

### 2.5 CoT 可控性与可监控性

与 GPT-5.4 同步发布了 **CoT-Control 评估套件**（13,000+ 任务），作为安全评估的重要组成部分：

- GPT-5.4 Thinking 具有**低 CoT 可控性**（low CoT controllability）
- 低可控性意味着模型难以刻意隐藏或操纵其推理过程
- OpenAI 承诺在未来系统卡片中同时报告 **CoT controllability** 和 **CoT monitorability**
- 不对前沿推理模型的 CoT 施加直接优化压力（not applying optimization pressure directly to CoTs）

---

## 三、风险缓解措施

### 3.1 网络安全风险缓解

作为首个"高"网络安全风险模型，OpenAI 部署了额外安全措施：

- 结构化安全测试，覆盖专业工作流、多步推理、系统枚举和约束下自监控
- 原生计算机使用引入新的风险面，需要专门的安全评估
- 维持与 GPT-5.3-Codex 相同的高网络安全风险分类框架

### 3.2 部署安全策略

- 延续 GPT-5 引入的 **safe-completions** 安全方法
- 从硬拒绝（hard refusal）转向以输出为中心的安全训练
- 系统级防护措施管理风险

---

## 四、关联分析

### 与 GPT-5.4 发布博文的关联

本系统卡片是 GPT-5.4 发布的配套安全文档。[GPT-5.4 发布博文](introducing_gpt_5_4.md)侧重于能力和产品定位，而系统卡片侧重于安全评估和风险分析。两者共同构成了对外的完整信息披露。

### 与 CoT Control 研究的关联

系统卡片中的 CoT 可控性评估直接引用了同日发布的 [CoT-Control 研究论文](cot_control_monitorability.md)。该研究提供了理论基础和评估方法论，系统卡片则展示了在 GPT-5.4 Thinking 上的实际评估结果。

### 与 Detecting Scheming 的关联

CoT 监控作为安全层，与此前发布的 [Detecting & Reducing Scheming](detecting_reducing_scheming_ai.md) 研究互补——前者关注模型能否隐藏推理意图，后者关注模型是否会产生欺骗性策略行为（scheming behavior）。

### 与 GPT-5 系列演进的关联

系统卡片序列：GPT-5.1 → GPT-5.2 → GPT-5.3 Instant → GPT-5.3-Codex → **GPT-5.4 Thinking**。网络安全风险评级从中等逐步上升至"高"，反映了模型能力增长带来的安全挑战也在同步升级。

### 与 Model Spec / Instruction Hierarchy 的关联

GPT-5.4 的安全框架建立在 **Model Spec**（模型行为规范，2026-03-25）和 **Instruction Hierarchy**（指令层级，2026-03-10）基础之上，定义了模型应遵循的行为准则和权限层级。

---

## 五、核心洞察

1. **"高"网络安全风险评级是里程碑事件**：标志着前沿模型能力已进入需要更严格安全管控的阶段，OpenAI 选择透明披露而非降级发布
2. **CoT 不可控性是安全优势**：推理模型天然难以操纵自身思维链，这使得 CoT 监控成为可靠的安全防线——安全性来自能力的"副产品"而非刻意设计
3. **能力-安全张力加剧**：GPT-5.4 Thinking 在部分类别可监控性下降，表明随着模型越来越强，维持全面安全监控的难度在增加
4. **计算机使用引入新风险维度**：原生 Computer Use 能力使模型从信息处理者变为环境操作者，安全评估需要覆盖全新的攻击面
5. **系统卡片制度趋于成熟**：从 GPT-5.1 到 GPT-5.4，OpenAI 的系统卡片已形成标准化的安全评估和披露流程，覆盖内容安全、网络安全、CBRN、可监控性等多维度

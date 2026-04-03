# Addendum: OpenAI o3 Operator — 计算机使用代理的 o3 升级

> 来源: https://openai.com/index/o3-o4-mini-system-card-addendum-operator-o3/
> 发布日期: 2025-05-23
> 类别: Safety - 系统卡片附录 / 计算机使用代理

---

## 一、核心概述

OpenAI 于 2025 年 5 月 23 日发布了 o3/o4-mini 系统卡片的附录（Addendum），专门针对 **o3 Operator**——一个基于 o3 模型微调的**计算机使用代理**（Computer-Using Agent, CUA）。这一升级将 Operator 产品（最初于 2025 年 1 月 23 日推出，基于 GPT-4o）的底层模型从 **GPT-4o 替换为 o3**，带来了更精确的浏览器交互和更强的推理能力。o3 Operator 通过**额外的安全数据微调**，引入了 Prompt Injection Monitor、Watch Mode 等多层安全机制。

> "o3 Operator replaces GPT-4o as the underlying model for the Computer-Using Agent, fine-tuned with additional safety data specifically for computer use scenarios."

---

## 二、关键技术细节

### 2.1 模型升级

| 维度 | CUA GPT-4o（旧） | CUA o3（新） |
|------|-----------------|-------------|
| **底层模型** | GPT-4o | o3 |
| **推理能力** | 标准 | 增强（o3 推理链） |
| **浏览器交互精度** | 基准 | 更精确的滚动、点击、输入 |
| **答案质量** | 基准 | 更结构化、更全面 |
| **安全训练** | 标准 | 额外的计算机使用安全数据微调 |
| **人类偏好** | 基准 | 在风格和清晰度上更受偏好 |

### 2.2 基准表现

o3 Operator 在多个基准上优于 GPT-4o 版本：
- **OSWorld**: 桌面/操作系统级自动化任务（表现提升）
- **WebArena**: 网页任务基准（表现提升）
- 具体数值分主要通过视频形式分享，未在公开文档中完整列出

### 2.3 三大安全风险类别

| 风险类别 | 描述 |
|---------|------|
| **Harmful Tasks（有害任务）** | 用户可能要求 Operator 执行有害操作 |
| **Model Mistakes（模型错误）** | 智能体在浏览/执行任务时可能犯错 |
| **Prompt Injections（提示注入）** | 网页上的恶意内容可能操纵模型行为 |

### 2.4 安全缓解措施

#### 针对有害任务
- o3 家族的**基线安全训练**（Baseline Safety Training）
- **智能体特定安全训练**（Agentic-Specific Safety Training）
- 人工与自动化**双重监控**
- **速率限制**（Rate Limits）遏制大规模滥用

#### 针对提示注入
- 模型经过**提示注入鲁棒性强化**（Robustified Against Prompt Injections）
- **Prompt Injection Monitor（提示注入监控器）**: 实时分析当前屏幕截图（screenshot），检测到可疑活动时自动**暂停执行**
- **Explicit User Confirmations（明确用户确认）**: 敏感操作前暂停并请求确认
- **Watch Mode（监视模式）**: 在高风险网站（如电子邮件、银行等）上强制启用，添加人在回路（human-in-the-loop）保障

#### 针对模型错误
- **Watch Mode** 覆盖高风险站点
- **拒绝执行最高风险任务**
- 在**最终确认交易前**要求用户确认

### 2.5 红队测试

- 红队测试覆盖：**越狱尝试**（jailbreak attempts）、**非浏览器界面上的有害错误**、**敏感任务确认遗漏**
- 使用 **100 个模拟真实用户任务的提示**进行测试（购物、邮件管理等）

---

## 三、关联分析

### 与 Operator（2025-01-23）的关系

o3 Operator 是 Operator 产品的**重大底层升级**。Operator 最初于 2025 年 1 月作为研究预览发布，使用 GPT-4o 作为底层 CUA 模型。4 个月后，o3 的推理能力和安全训练带来了质的飞跃。这一升级路径（GPT-4o → o3）体现了 OpenAI 在智能体产品上的**快速迭代策略**。

### 与 o3/o4-mini 系统卡片（2025-04-16）的关系

本附录是 o3/o4-mini 系统卡片的补充文档，专注于 o3 在**计算机使用场景**下的安全评估。主系统卡片覆盖模型的通用安全评估，而附录深入分析了智能体特定的风险和缓解措施。

### 与 ChatGPT Agent（2025-07-17）的前置关系

o3 Operator Addendum 建立的安全框架——Prompt Injection Monitor、Watch Mode、用户确认机制——成为两个月后发布的 [ChatGPT Agent](introducing_chatgpt_agent.md) 安全体系的基础。ChatGPT Agent 继承并扩展了这些安全措施，同时将 Operator 的浏览器操控能力整合进 ChatGPT 主界面。

### 与 Codex（2025-05-16）的同期关系

o3 Operator Addendum 发布于 Codex 发布一周后。两者都基于 o3 系列模型，但面向不同领域：Codex 聚焦**软件工程**（沙箱代码执行），Operator 聚焦**网页浏览和 GUI 操作**。两者共同展示了 o3 在不同智能体场景下的适用性。

### 与 Codex Figma 集成的关联

后续的 [Codex Figma](codex_figma_design_code_integration.md) 集成（2026-02-26）进一步扩展了 AI 智能体与 GUI 工具的交互模式。o3 Operator 开创了"AI 操控 GUI"的产品化路径，Codex Figma 则将这种理念延伸到了设计工具领域。

---

## 四、核心洞察

1. **GPT-4o → o3 的架构升级逻辑**: 将底层模型从通用模型（GPT-4o）升级为推理模型（o3），反映了计算机使用代理对**深度推理能力**的核心需求——浏览网页、理解 GUI、执行多步操作本质上是推理密集型任务
2. **Prompt Injection Monitor 的屏幕截图分析**: 通过实时分析浏览器屏幕截图来检测提示注入，是一种创新的安全方法——将视觉理解能力用于安全防御，而非仅依赖文本层面的检测
3. **Watch Mode 的风险分层策略**: 不同网站有不同风险等级（邮件 > 购物 > 信息浏览），Watch Mode 根据站点类型动态调整监控强度，实现了安全与可用性的平衡
4. **"额外安全数据微调"的范式**: 不是简单地将 o3 应用于计算机使用场景，而是用**智能体特定的安全数据进行额外微调**，表明 OpenAI 认为通用安全训练不足以覆盖智能体场景的安全需求
5. **100 个真实任务提示的评估方法**: 使用模拟真实用户行为的测试集（而非人造对抗性样本）进行安全评估，体现了对实际部署场景风险的关注

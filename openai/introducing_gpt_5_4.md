# Introducing GPT-5.4

> 来源: https://openai.com/index/introducing-gpt-5-4/
> 发布日期: 2026-03-05
> 类别: Research - 模型发布

---

## 一、核心概述

GPT-5.4 是 OpenAI 于 2026 年 3 月 5 日发布的最新旗舰模型，定位为**"the most capable and efficient frontier model for professional work"**（最强大且最高效的前沿专业工作模型）。

核心创新在于**首次将通用推理能力与行业领先的编码能力合并为单一统一系统**（unified system），不再将 Codex 作为独立的编码模型，而是将编码能力原生整合到模型中，与计算机使用（Computer Use）和知识工作能力协同运作。

---

## 二、关键特性

### 2.1 Tool Search（工具搜索）

GPT-5.4 引入了全新的 **Tool Search** API 能力，使模型在面对大量工具时能高效选择和调用。

- 实现 **47% 的 token 削减**，显著提高成本效益
- Toolathlon 基准：**54.6%**（vs GPT-5.2: 46.3%，提升 +8.3%）

> "A new API capability that allows models to work efficiently when given many tools."

### 2.2 GDPval 基准突破

在 GDPval（衡量 AI 在 44 个职业中的真实工作表现）上：
- **GPT-5.4: 83.0%** 匹配或超越行业中期专业人士
- **GPT-5.2: 70.9%**
- **提升幅度: +12.1 个百分点**

### 2.3 原生计算机使用能力（Computer Use）

GPT-5.4 是 OpenAI **首个具有原生计算机使用能力的通用模型**（first general-purpose model with native computer-use capabilities）：
- 审查屏幕截图并执行点击、输入、导航等操作
- 像人类用户一样操作浏览器和应用程序
- 实验性 Codex 技能 **"Playwright (Interactive)"** 用于浏览器自动化
- **OSWorld-Verified: 75.0%**

### 2.4 CoT Controllability（思维链可控性）

与 GPT-5.4 一同发布了 **CoT-Control 评估套件**（13,000+ 任务，24 个环境），衡量模型是否能刻意混淆推理以逃避监控：
- GPT-5.4 Thinking 具有**低 CoT 可控性** — 难以刻意隐藏推理
- 低可控性被视为 AI 安全的积极信号（positive safety signal）
- OpenAI 承诺在未来系统卡片中同时报告 CoT controllability 和 CoT monitorability

### 2.5 事实准确性改进

- 单个声明虚假概率**降低 33%**（individual claims are 33% less likely to be false）
- 完整回复包含错误的概率**降低 18%**

---

## 三、基准测试全景

| 基准 | GPT-5.4 | GPT-5.2 | 说明 |
|------|---------|---------|------|
| GDPval | 83.0% | 70.9% | 44 职业专业工作 |
| SWE-Bench Pro | 57.7% | - | 软件工程 |
| MMMU Pro | 81.2% | - | 多模态理解 |
| OSWorld-Verified | 75.0% | - | 计算机使用 |
| BrowseComp | 89.3% | - | 网页浏览 |
| Toolathlon | 54.6% | 46.3% | 多步工具使用 |

---

## 四、模型变体与定价

| 变体 | 特点 | 上下文窗口 |
|------|------|-----------|
| GPT-5.4 | 标准版，专业工作 | 272K tokens |
| GPT-5.4 Thinking | 深度推理变体 | 1M tokens (实验性) |
| GPT-5.4 Pro | 高性能变体，最难任务 | 1.05M tokens |
| GPT-5.4 Mini | 6x 更便宜，94% 编码性能 | 1.05M tokens |

---

## 五、与前代模型对比

### GPT-5.4 vs GPT-5.3

- GPT-5.3 定位为聊天导向（chat-oriented），GPT-5.4 定位为专业工作
- GPT-5.4 将 GPT-5.3-Codex 的编码能力完全整合，不再隔离
- GPT-5.4 新增原生计算机使用能力

### GPT-5.4 vs GPT-5.2

- GDPval: 83.0% vs 70.9%（+12.1%）
- Toolathlon: 54.6% vs 46.3%（+8.3%）
- 事实性大幅提升（-33% 虚假声明）
- 新增 Tool Search、Computer Use 等能力

---

## 六、关联分析

### 与 Model Spec / Instruction Hierarchy 的关联

GPT-5.4 的安全框架建立在此前发布的 **Model Spec**（模型行为规范）和 **Instruction Hierarchy**（指令层级）基础之上。Model Spec 定义了"指令链"（Chain of Command）的权限级别，而 GPT-5.4 的 CoT 可控性研究进一步验证了推理链监控作为安全层的可行性。

### 与 Codex 生态的演进

从 GPT-5.2-Codex（独立编码模型）→ GPT-5.3-Codex（增强版独立模型）→ GPT-5.4（编码能力原生整合），体现了 OpenAI 从"专用模型"向"统一模型"的架构演进路线。这与 GPT-5 发布时提出的"统一系统架构"（unified system architecture）理念一脉相承。

### 与 Safe-Completions 的关联

GPT-5.4 延续了 GPT-5 引入的 **safe-completions** 安全方法——从硬拒绝转向以输出为中心的安全训练，在保持高可用性的同时严格遵守安全策略。

### 与 GDPval 基准的关联

GDPval 是与 GPT-5.4 同步发布的新型评估框架，代表了从学术基准（MMLU）到经济价值导向基准的范式转变。详见 [GDPval 总结](gdpval_real_world_benchmark.md)。

---

## 七、核心洞察

1. **统一化趋势**：GPT-5.4 标志着 OpenAI 从"多个专用模型"向"单一统一模型"的战略转型完成
2. **Computer Use 成为标配**：原生计算机使用能力使 AI 从"对话工具"进化为"操作代理"
3. **安全与能力并进**：CoT 可控性研究表明，推理模型天然难以隐藏推理过程，这为 AI 安全监控提供了积极基础
4. **工具生态成熟**：Tool Search 功能解决了大规模工具调用的效率问题，为复杂 Agent 系统铺平道路

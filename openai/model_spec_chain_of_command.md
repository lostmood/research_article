# Inside Our Approach to the Model Spec

> 来源: https://openai.com/index/inside-our-approach-to-the-model-spec/
> Model Spec 文档: https://model-spec.openai.com/2025-12-18.html
> 发布日期: 2026-03-25
> 类别: Safety - AI 行为治理框架

---

## 一、核心概述

OpenAI 深入介绍了 **Model Spec（模型规范）** 框架——一份公开的正式文档，定义了 AI 模型应如何行为。该框架被外界评为"迄今为止最详细的 AI 行为治理公开尝试"。核心创新是 **Chain of Command（指令链）** 机制，为来自不同来源的指令分配明确的权限级别，解决指令冲突、尊重用户自由并确保安全优先。

---

## 二、Chain of Command（指令链）层级

Model Spec 建立了清晰的四级指令优先级体系：

### 2.1 Root-level Instructions（根级指令）— 最高优先级

- 适用于**所有模型实例**的固定规则
- 主要为**禁止性规则**，模型必须避免：
  - 造成灾难性风险的行为
  - 直接物理伤害
  - 违法行为
  - 破坏指令链本身
- **不可被任何开发者或用户覆盖**

### 2.2 System/Developer-level Instructions（系统/开发者级指令）

- 由平台开发者通过 **system messages** 设置
- 可为特定应用定制模型行为
- 受根级规则约束

### 2.3 User-level Instructions（用户级指令）

- 模型应尊重用户请求，**除非**与更高级别指令冲突
- 体现了对用户自由的尊重原则

### 2.4 Defaults（默认行为）

- 包含根级规则和用户/指南级默认值
- 可被用户或开发者在适当范围内覆盖

> **优先级顺序**: Root > System/Developer > User > Defaults

---

## 三、安全边界与红线原则

### 3.1 Red-line Principles（红线原则）

绝对不可逾越的硬性安全边界：
- **永不**生成 CSAM（儿童性虐待材料）
- **永不**协助制造大规模杀伤性武器
- **永不**提供可直接导致严重物理伤害的指导

### 3.2 三类伤害识别

Model Spec 明确界定三类潜在伤害：

1. **遵循用户指令导致的伤害** — 如自残指导、暴力行为
2. **遵循开发者指令与安全冲突** — 开发者定制行为可能带来的风险
3. **Prompt Injection（提示注入）攻击** — 对抗性输入试图覆盖指令层级

### 3.3 通用保护规则

- 对未成年用户适用更严格标准："不鼓励自残、妄想或躁狂"
- **避免信息危害（Info Hazards）**: 危险信息请求触发硬性安全边界

---

## 四、核心治理原则

### 4.1 客观性承诺

- 在第一方部署（如 ChatGPT）中，系统消息**不会故意损害客观性**
- 明确承诺模型响应为**用户利益**优化，而非收入或参与度指标

### 4.2 用户自由尊重

- 在安全边界内最大化用户自主权
- 默认行为可被用户合理覆盖
- 体现"**既安全又有用**"的平衡理念

### 4.3 Agentic AI（智能体 AI）治理

- 随着 AI 自主性增强（订机票、写代码、管理工作流），治理挑战从"**模型应该说什么**"转向"**模型应该做什么**"
- Model Spec 提供了**控制副作用（Side Effects）** 和**限定自主范围（Scoping Autonomy）** 的指导
- OpenAI 承认这是框架中**最不成熟的领域**

---

## 五、可度量的合规性

Model Spec 的一个关键特点是**规范足够精确，合规性可被量化**：
- OpenAI 可以对照 Spec **为模型评分**
- 这使得安全治理从定性判断转向**定量评估**
- 为行业提供了可复制的治理蓝图

---

## 六、关联分析

### 与 Instruction Hierarchy / IH-Challenge 的关联

**Improving Instruction Hierarchy in Frontier LLMs**（2026-03-10）的 IH-Challenge 训练数据集直接基于 Model Spec（2025-12-18 版本）的指令层级设计。IH-Challenge 将 Model Spec 的理论框架转化为可训练的 RL 数据集，使模型在实践中遵循 `system > developer > user > tool` 的优先级。两者是**理论与实践**的关系。

### 与 Deliberative Alignment 的关联

2024 年 12 月发布的 **Deliberative Alignment** 研究教导 o1 系列模型在推理过程中显式参考安全规范。Model Spec 正是这些安全规范的**正式文档化版本**，为审慎对齐提供了结构化的规则基础。

### 与 Detecting Scheming 的关联

**Detecting and Reducing Scheming in AI Models** 中的 Anti-Scheming Spec（反欺骗规范）仿照 Model Spec 设计，包含 9 项原则。Model Spec 的指令链机制确保模型"不破坏指令链本身"，与反欺骗训练形成**互补防御**。

### 与 GPT-5.4 的关联

GPT-5.4 作为最新旗舰模型，其行为规范直接受 Model Spec 约束。Model Spec 是所有 OpenAI 模型行为的**顶层治理文件**。

---

## 七、核心洞察

1. **指令链是安全基石**: Chain of Command 不仅是理论概念，而是可落地、可训练、可度量的工程方案，为 prompt injection 防御和 scheming 检测提供了统一框架
2. **安全与自由的精确平衡**: Model Spec 通过分层权限实现"既不过度拒绝，也不违反安全"的精确平衡，避免了简单的"全拒绝"或"全放行"
3. **Agentic 领域是下一个挑战**: OpenAI 坦承智能体行为治理最不成熟，随着 Codex、ChatGPT Agent 等产品落地，这将是 Model Spec 演进的核心方向
4. **行业治理蓝图**: Model Spec 的公开发布意味着 OpenAI 在安全治理领域从"各自为政"走向"公共标准"，可能影响整个行业的 AI 行为规范制定
5. **从定性到定量**: 规范的精确性使安全评估可量化，这是 AI 安全从研究走向工程化的关键一步

# GPT-5.3-Codex System Card

> 来源: https://openai.com/index/gpt-5-3-codex-system-card/
> System Card PDF: https://cdn.openai.com/pdf/23eca107-a9b1-4d2c-b156-7deb4fbc697c/GPT-5-3-Codex-System-Card-02.pdf
> Deployment Safety Hub: https://deploymentsafety.openai.com/gpt-5-3-codex
> 发布日期: 2026-02-05
> 类别: Safety - 模型系统卡与部署安全

---

## 一、核心概述

OpenAI 发布了 **GPT-5.3-Codex** 的 System Card，这是 OpenAI 首个在 **Preparedness Framework（准备框架）** 下被评定为**网络安全领域"High"（高）能力阈值**的模型。该评级触发了一整套分层安全部署措施，包括 **Safety Reasoner（安全推理器）**、**双层自动化监控**和 **Trusted Access Program（可信访问计划）**。同时该模型在生物安全领域也被评定为"High"能力，与 GPT-5 家族其他模型一致。

---

## 二、Preparedness Framework 评级

### 2.1 网络安全 — "High"（高）

- **首个**获得网络安全领域"High"评级的 OpenAI 模型
- 意味着模型具备**高级网络攻击辅助能力**
- 根据 Preparedness Framework 规定，"High"评级的模型**不得在未实施充分安全措施前发布**

### 2.2 生物安全 — "High"（高）

- 与 GPT-5 家族其他模型一致
- 生物安全控制措施首先在 **ChatGPT Agent** 上实施（首个达到"High"生物能力的系统）
- GPT-5.3-Codex 的网络安全措施**平行于**已有的生物安全控制

### 2.3 其他领域

- 化学、放射/核、说服力等领域的评级在 System Card 中有详细说明

---

## 三、分层安全堆栈（Layered Safety Stack）

### 3.1 Safety Reasoner（安全推理器）

- **集成于模型管道**的安全分类系统
- 对用户 prompt 和模型生成内容进行**实时分类**
- 识别并阻止：
  - **高风险双用途（Dual-use）请求** — 可用于攻击也可用于防御的网络安全操作
  - **直接有害行为** — 明确的恶意网络攻击请求
- **红队测试历程**：
  - 2025 年 12 月: 在 GPT-5.2-thinking 上开始测试
  - 2026 年 1 月: 在 GPT-5.2-Codex 上继续测试
  - 2026 年 2 月: 在 GPT-5.3-Codex 上正式部署

### 3.2 Two-Tiered Automated Oversight（双层自动化监控）

- **第一层**: 实时监控，阻止不安全的网络安全 prompt 和生成内容
- **第二层**: 深度分析，检测高风险双用途活动和有害行为模式
- 两层协同工作，提供**纵深防御**

### 3.3 Traffic Routing（流量路由）

- 部分高风险流量被**路由到能力较低的模型**处理
- 降低了最高能力模型被滥用的风险
- 实现了**能力与风险的动态匹配**

### 3.4 模型级拒绝与降级

- 模型被训练为对有害网络安全请求**主动拒绝或降级（De-escalate）**
- 不仅仅是外部过滤，而是模型**内在行为**的一部分

---

## 四、Trusted Access Program（可信访问计划）

### 4.1 设计理念

- 基于身份验证的**门控访问程序**
- 目的：将高风险网络安全能力**限制给合法安全专业人员**
- 减少恶意用户获取高级能力的风险

### 4.2 支持的合法用例

| 用例 | 说明 |
|------|------|
| **Penetration Testing（渗透测试）** | 授权的安全测试 |
| **Red Teaming（红队测试）** | 模拟攻击者视角的安全评估 |
| **Vulnerability Assessment & Exploitation（漏洞评估与利用）** | 发现和验证安全漏洞 |
| **Security Testing / Detection Evasion（安全测试/检测绕过）** | 测试防御系统的有效性 |
| **Malware Reverse Engineering（恶意软件逆向工程）** | 分析恶意软件行为 |
| **Cryptographic Research（密码学研究）** | 密码学安全研究 |

### 4.3 资源投入

- OpenAI 承诺投入 **1000 万美元 API 额度**用于加速网络防御
- 由 CEO Sam Altman 公开宣布

---

## 五、红队测试与评估

### 5.1 测试时间线

| 时间 | 模型 | 活动 |
|------|------|------|
| 2025-12 | GPT-5.2-thinking | Safety Reasoner 初始测试 |
| 2026-01 | GPT-5.2-Codex | Safety Reasoner 持续测试 |
| 2026-02 | GPT-5.3-Codex | 正式发布，完整安全评估 |

### 5.2 评估内容

- 网络安全能力的**详细能力评估**
- Safety Reasoner 的**有效性验证**
- 对抗性测试：尝试绕过安全措施的各种攻击向量
- 双用途场景的**边界判断**测试

---

## 六、法律与合规挑战

- **Midas Project** 声称 OpenAI 未能为被评为高网络安全风险的模型实施法律要求的安全措施
- 引发了关于**加州 AI 安全法**合规性的讨论
- GPT-5.3-Codex 成为 AI 安全监管的**标志性案例**

---

## 七、关联分析

### 与 GPT-5.4 的关联

**GPT-5.4** 作为后续旗舰模型，继承并扩展了 GPT-5.3-Codex 建立的安全架构。GPT-5.3-Codex 的分层安全堆栈为后续模型提供了**可复用的安全基础设施**。

### 与 Instruction Hierarchy / IH-Challenge 的关联

GPT-5.3-Codex 的 Safety Reasoner 需要强大的**指令层级遵循能力**来正确处理高风险双用途请求。**IH-Challenge**（2026-03）的训练方法直接支撑了 Safety Reasoner 对合法 vs. 恶意请求的区分能力。

### 与 Detecting Scheming 的关联

在网络安全领域达到"High"能力意味着模型如果发生 **scheming（策略性欺骗）**，后果将更为严重。**Detecting and Reducing Scheming** 的反欺骗训练为高能力模型提供了**额外的安全保障层**。

### 与 Codex 生态的关联

**Introducing Codex** 和 **Codex Figma** 展示了 Codex 系列的产品化方向。GPT-5.3-Codex System Card 揭示了这些强大编码能力背后的**安全代价和治理复杂性**。

### 与 GPT-5.4 Thinking System Card 的关联

GPT-5.4 Thinking SC 的安全评估延续了 GPT-5.3-Codex 建立的评估方法论和安全框架，形成了从 5.3 到 5.4 的**安全评估连续性**。

### 与 CoT Control 的关联

**CoT Controllability** 研究提供的可监控性能力，在 GPT-5.3-Codex 这类高风险模型上尤为关键。思维链的不可控性（对模型有利）使得安全监控系统可以检测模型是否在尝试**绕过安全推理器**。

---

## 八、核心洞察

1. **"High"评级是双刃剑**: 网络安全"High"能力既代表了强大的编码和安全研究能力，也意味着前所未有的滥用风险，OpenAI 选择了"有条件发布"而非"不发布"
2. **分层防御是高能力模型的必然**: 单一安全措施不足以应对"High"能力模型的风险，Safety Reasoner + 双层监控 + 流量路由 + 可信访问形成了**纵深防御体系**
3. **身份验证是能力门控的关键**: Trusted Access Program 将安全从"能力限制"转向"访问控制"，承认高能力对安全专业人员有正当价值
4. **1000万美元网络防御投入**: 将安全承诺量化为具体资源投入，体现了 OpenAI 对"AI 赋能防御"的战略重视
5. **监管压力推动安全实践**: Midas Project 的法律挑战表明，AI 安全不再仅是技术问题，已进入**法律合规**领域，System Card 的详细程度部分反映了合规需求
6. **Safety Reasoner 的迭代演进**: 从 GPT-5.2-thinking 到 GPT-5.3-Codex 的三个月迭代，展示了安全组件的**渐进式开发和测试**方法论

# ChatGPT Agent System Card — 自主多步骤智能体的安全评估

> 来源: https://openai.com/index/chatgpt-agent-system-card
> 发布日期: 2025-07-17
> 类别: Safety - 系统卡片 / 红队测试

---

## 一、核心概述

OpenAI 于 2025 年 7 月 17 日同步发布了 ChatGPT Agent System Card，作为 ChatGPT Agent 产品发布的配套安全文档。这是 OpenAI 迄今为止**最全面的智能体安全评估**，涵盖了针对自主多步骤智能体（能浏览网页、执行终端命令、访问第三方应用）的系统性风险分析和缓解措施。核心亮点包括：**16 位 PhD 安全研究人员的红队测试**、**生物化学风险的"高"评级**、以及针对提示注入（prompt injection）的多层防御体系。

> "The most comprehensive safety assessment for an autonomous agent — 16 PhD red teamers, 'High' biological risk classification, and multi-layered prompt injection defenses."

---

## 二、关键技术细节

### 2.1 红队测试（Red Teaming）

#### PhD 级别安全研究
- **16 位 PhD 安全研究人员**，每人投入 **40 小时**进行系统性攻击测试
- 发现 **7 种通用漏洞利用**（universal exploits）可能危及系统
- **110 次额外攻击**由 OpenAI 更广泛的红队网络执行

#### 生物安全专项测试
- **7 位生物安全/生物安全保障领域专家**，每人投入 **3-5 小时**
- 测试对象为 **"helpful-only"版本**（仅回答有帮助的版本，移除安全限制），评估模型在潜在危险生物任务上的能力
- 测试涵盖**智能体模式和非智能体模式**两种场景

### 2.2 生物化学风险评估

#### Preparedness Framework 评级
- ChatGPT Agent 被分类为**生物能力"高"（High）**——这是**预防性决定**，即使没有确凿证据证明模型已跨越该阈值
- 这一评级触发了额外的安全保障措施

#### 外部评估
- **SecureBio** 进行了独立的外部评估，使用多个专业基准：

| 基准测试 | 评估维度 |
|---------|---------|
| **VCT（Virology Capabilities Test）** | 病毒学能力 |
| **HPCT（Human Pathogen Capabilities Test）** | 人类病原体能力 |
| **MBCT（Molecular Biology Capabilities Test）** | 分子生物学能力 |
| **WCB（World-Class Biology）** | 世界级生物学 |
| **Fragment Design** | 片段设计 |
| **Pathogen Acquisition** | 病原体获取 |
| **Biodesign Tool Use** | 生物设计工具使用 |

#### 智能体 + 互联网浏览的风险放大
- 模型的**互联网浏览能力**增加了生物学能力提升（biological uplift）评估的复杂性
- 自主智能体能主动搜索并综合信息，这与静态问答模型的风险模型截然不同

### 2.3 模型安全训练评估

| 评估场景 | ChatGPT Agent | o4-mini（对比） |
|---------|--------------|----------------|
| **挑战性生物安全提示** | not_unsafe: **0.879** | not_unsafe: 0.779 |
| **对抗性生产提示** | not_unsafe: **0.969** | not_unsafe: 0.905 |

- ChatGPT Agent 在两项安全指标上均**显著优于** o4-mini

### 2.4 系统级安全防护

#### 生物安全专项防护
| 防护层 | 机制 |
|--------|------|
| **Biological Topical Classifier（生物主题分类器）** | 识别和标记生物相关对话 |
| **Reasoning Model Review（推理模型审查）** | 对生物相关内容进行深度推理审查 |

#### 提示注入防御（Prompt Injection Defense）
| 指标 | 表现 |
|------|------|
| **可视化浏览器攻击** | **95%** 被拦截 |
| **数据泄露尝试** | **78%** 被捕获 |
| **交互监控** | **每一次交互**都被监控 |

#### 核心防御机制
- **Prompt Injection Monitor（提示注入监控器）**: 实时分析当前屏幕截图，检测可疑活动时暂停执行
- **Watch Mode（监视模式）**: 在高风险网站（如电子邮件）上启用人在回路（human-in-the-loop）保障
- **Explicit User Confirmations（明确用户确认）**: 敏感操作前要求用户确认
- **Rate Limits（速率限制）**: 限制请求频率以遏制滥用

---

## 三、关联分析

### 与 ChatGPT Agent 产品发布的配套关系

System Card 与 [Introducing ChatGPT Agent](introducing_chatgpt_agent.md) 同日发布，遵循 OpenAI 的 **"能力与安全同步发布"** 原则。Agent 的每一项新能力（远程浏览、终端执行、应用连接器）都在 System Card 中有对应的风险分析和缓解措施。

### 与 o3 Operator Addendum 的安全框架延续

[o3 Operator Addendum](o3_operator_addendum.md)（2025-05-23）建立的安全框架——Prompt Injection Monitor、Watch Mode、用户确认机制——在 ChatGPT Agent System Card 中得到了继承和扩展。从 Operator 到 ChatGPT Agent，安全措施经历了系统性的升级。

### 与 Detecting & Reducing Scheming AI 的关联

OpenAI 的 [Detecting & Reducing Scheming AI](detecting_reducing_scheming_ai.md) 研究关注模型是否会策略性地规避安全控制。ChatGPT Agent 作为自主智能体拥有更大的行动自由度，其 System Card 中的多层监控机制（特别是 Prompt Injection Monitor 的实时屏幕分析）可视为对 scheming 风险的实际应对。

### 与 Monitor Internal Coding Agents 的关联

OpenAI 内部编码智能体监控研究（2026-03-19）提供的监控方法论，与 ChatGPT Agent System Card 中的监控策略有共通之处——都强调对自主智能体行为的实时观察和异常检测。

### 与 Codex System Card Addendum 的对比

Codex 有自己的 System Card Addendum（o3/o4-mini Codex Addendum），聚焦于**代码执行安全**和沙箱隔离。而 ChatGPT Agent System Card 的风险面更广——涵盖网络浏览、信息泄露、生物化学风险等通用智能体场景。两者共同构成 OpenAI 智能体安全文档体系。

---

## 四、核心洞察

1. **红队测试的规模化与专业化**: 16 位 PhD + 40 小时/人的投入，加上 7 位生物安全专家的专项测试，代表了 AI 智能体安全评估的新标准——评估成本和时间与模型训练本身开始可比
2. **"预防性高风险评级"的决策哲学**: 在缺乏确凿证据的情况下主动升级风险等级，体现了 OpenAI 从"证据驱动"向"预防驱动"的安全策略转变——对自主智能体采取更保守的评估标准
3. **互联网浏览的风险乘数效应**: 智能体的网络浏览能力使传统的静态能力评估失效——模型不仅拥有训练时获得的知识，还能主动搜索和综合新信息，这是全新的风险维度
4. **95% 的提示注入拦截率意味着 5% 的漏洞**: 在自主智能体场景下，5% 的漏网率可能意味着在大规模部署中有显著数量的成功攻击，这凸显了提示注入防御的持续挑战
5. **安全评估从"模型级"到"系统级"的演进**: System Card 不仅评估模型本身，还评估整个系统（模型 + 工具 + 浏览器 + 监控器），反映了智能体安全评估需要系统思维

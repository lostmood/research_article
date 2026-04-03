# GPT-5.2-Codex System Card Addendum

> 来源: [OpenAI Blog](https://openai.com/index/gpt-5-2-codex-system-card-addendum/)
> 发布日期: 2025-12-18
> 类别: Safety / System Card / Agentic Coding

---

## 核心概述

OpenAI 发布了 **GPT-5.2 System Card 的补充文档（Addendum）**，专门针对编码优化版本 **GPT-5.2-Codex** 的安全评估和防护措施。GPT-5.2-Codex 被描述为 OpenAI "迄今最先进的智能体编码模型（most advanced agentic coding model）"，专为复杂、真实世界的软件工程任务设计。该补充文档重点覆盖了 **智能体沙箱安全（Agentic Sandbox Safety）**、**网络安全防护（Cybersecurity Defenses）** 和 **恶意代码拒绝（Malware Refusal）** 等专项安全措施。在 **Preparedness Framework（准备框架）** 下，该模型被评估为 **"Capable（有能力）"** 但未达到 **"High（高）"** 风险阈值。

---

## 关键技术细节

### 安全评估结果

| 评估维度 | 结果 |
|----------|------|
| **Preparedness Framework 评级** | "Capable" — 有能力但未达"High"阈值 |
| **Malware Refusal Rate（恶意代码拒绝率）** | **100%** — 拒绝所有恶意代码相关请求 |
| **Prompt Injection Robustness（提示注入鲁棒性）** | 相比前代模型显著增强 |
| **Jailbreak Resistance（越狱抵抗力）** | 改进的越狱防御能力 |
| **Hallucination Rate（幻觉率）** | 较低 |

### 智能体沙箱安全（Agentic Sandbox Safety）

- 代码执行在 **沙箱环境（Sandboxed Execution Environment）** 中运行
- 模型设计为 **配合策略控制（Cooperate with Policy Controls）** 而非绕过它们
- 集成到现有工程工作流（IDE、CI/CD、代码审查系统）

### 网络安全评估（Cybersecurity Evaluation）

- 在 **Capture the Flag（CTF）** 挑战中表现为 OpenAI 最强的网络安全模型
- 核心能力归因于 **Context Compaction（上下文压缩）**：能够跨多个上下文窗口连贯工作
- 实际案例：用于调查 **React2Shell 漏洞（CVE-2025-55182）**，发现了此前未知的漏洞

### 网络安全防护体系

| 防护层 | 说明 |
|--------|------|
| **Two-Tiered Automated Oversight（两层自动化监督）** | 实时监控和拦截不安全的网络安全提示 |
| **Trusted Access Control (TAC)** | 对高风险网络安全用例（渗透测试、红队、恶意代码逆向工程、安全测试）进行门控 |
| **Traffic Routing（流量路由）** | 高风险流量路由到能力较弱的模型，以阻断威胁行为者 |
| **Prompt Handling & Redaction（提示处理与编辑）** | 安全的提示处理和敏感信息编辑机制 |

### 模型能力

- 优化用于 **长期、真实世界软件工程任务**
- 支持 **防御性网络安全工作流（Defensive Cybersecurity Workflows）**
- 可通过 ChatGPT 付费版的 Codex 界面和 API 访问

---

## 关联分析

| 关联主题 | 说明 |
|----------|------|
| **GPT-5.2 System Card** | 本文档是 GPT-5.2 System Card 的补充，聚焦编码场景 |
| **Preparedness Framework** | OpenAI 的前沿能力风险评估框架 |
| **Agentic Coding** | 智能体式编码范式，模型使用工具、终端和上下文迭代完成任务 |

### 与其他 OpenAI 产品/文档的关系

- **GPT-5.2 System Card (2025-12-11)** — 本文档的基础文档，提供 GPT-5.2 全面的安全评估
- **GPT-5.3-Codex System Card (2026-02-05)** — 后续升级版本的安全评估
- **GPT-5.1-Codex-Max (introducing_gpt_5_1_codex_max.md)** — 前代 Codex 编码模型
- **Codex (2025-05-16)** — Codex 产品的初始发布
- **Codex Figma (codex_figma_design_code_integration.md)** — Codex 在设计-代码集成中的应用
- **safe-completions (2025-08)** — 安全补全相关的早期工作

---

## 核心洞察

1. **"Capable 但非 High"的风险定位**：Preparedness Framework 下的评级表明，GPT-5.2-Codex 在网络安全等领域具备显著能力，但 OpenAI 评估认为尚未达到需要限制部署的"高"风险阈值。这一评级既是能力声明也是安全承诺。

2. **100% 恶意代码拒绝率的工程意义**：实现完全的恶意代码拒绝是一个重要的安全工程成就，说明 OpenAI 在编码模型的安全对齐上投入了大量专项工作。

3. **网络安全的双刃剑治理**：GPT-5.2-Codex 既是强大的防御性网络安全工具（CTF 评估最优），又可能被滥用于攻击。OpenAI 通过 TAC 门控、两层监督和流量路由构建了多层防护，这是处理"双重用途（Dual-Use）"能力的工程范本。

4. **Context Compaction 是智能体编码的关键技术**：能够跨多个上下文窗口连贯工作的能力，使模型能够处理长时间的软件工程会话，这对于真实世界的编码任务至关重要。

5. **从模型安全到系统安全**：该补充文档展示了安全评估从单纯的模型层面扩展到了包括沙箱、监督系统、访问控制和流量路由在内的完整系统层面，反映了智能体安全的复杂性。

# GPT-5.1-Codex-Max System Card

## 基本信息
- **来源**: OpenAI Safety
- **发布日期**: 2025-11-19
- **链接**: https://openai.com/index/gpt-5-1-codex-max-system-card/
- **类别**: 安全评估 / 系统卡片（System Card）

## 核心概述

GPT-5.1-Codex-Max 系统卡片详细介绍了该前沿代理编码模型的安全评估、风险缓解措施和部署保障。重点涵盖 **提示注入（Prompt Injection）** 防御和 **网络安全能力（Cybersecurity Capabilities）** 的安全缓解，采用双层自动化监督（Two-Tiered Automated Oversight）架构实现实时监控和拦截。

## 关键技术细节

### 1. 安全架构：双层自动化监督（Two-Tiered Automated Oversight）
- **第一层**: 实时监控高风险双重用途（Dual-Use）使用场景
- **第二层**: 自动拦截不安全的网络安全相关提示和生成内容
- 模型级安全缓解（Model-Level Mitigations）内置于模型训练中

### 2. 提示注入（Prompt Injection）防御
- 明确警告启用互联网访问会引入来自不受信任内容的提示注入风险
- 建议在大多数场景维持 **受限模式（Restricted Mode）** 以缓解此风险
- 模型训练中强化了对注入攻击的抵抗能力

### 3. 网络安全能力评估
- GPT-5.1-Codex-Max 是 OpenAI 当时部署的 **最具网络安全能力的模型**
- CTF（Capture The Flag）挑战表现从 GPT-5 的 27% 提升至 **76%**
- 根据 OpenAI 准备度框架（Preparedness Framework），尚未达到"高"（High）级别的网络安全能力阈值
- OpenAI 按"每个新模型都可能达到'高'级别网络安全能力"的假设进行规划和评估

### 4. 可信访问控制（Trusted Access Controls, TAC）
基于身份的门控程序，支持的合规用例包括：
- **渗透测试（Penetration Testing）**
- **红队测试（Red Teaming）**
- **漏洞评估（Vulnerability Assessment）**
- **安全测试/检测规避（Security Testing/Detection Evasion）**
- **恶意软件逆向工程（Malware Reverse Engineering）**
- **密码学研究（Cryptographic Research）**

### 5. 网络安全防控措施
- 训练模型 **拒绝或降级处理** 有害网络行为请求
- 高风险流量 **路由至能力较弱的模型** 处理
- **威胁情报驱动的调查与检测** 系统
- 与 ChatGPT Agent 生物安全控制并行的方法论

### 6. 安全基线指标
与 GPT-5 系列安全指标对比（not_unsafe 越高越好）：

| 类别 | gpt-5 (8月) | gpt-5 (10月) |
|---|---|---|
| 非暴力仇恨 | 0.800 | 0.853 |
| 个人数据 | 0.876 | 0.908 |
| 骚扰/威胁 | 0.653 | 0.706 |
| 色情/剥削 | 0.785 | 0.910 |
| 色情/未成年人 | 0.906 | 0.959 |
| 极端主义 | 0.933 | 0.925 |

### 7. 越狱评估（Jailbreak Evaluations）
| 类别 | gpt-5 (8月) | gpt-5 (10月) |
|---|---|---|
| 非法/非暴力犯罪 | 0.926 | 0.957 |
| 暴力 | 0.942 | 0.968 |
| 滥用/虚假信息/仇恨 | 0.967 | 0.981 |
| 色情内容 | 0.954 | 0.969 |

## 关联分析

### 与 OpenAI 安全体系
- **准备度框架 v2（Preparedness Framework v2）**: 系统卡片遵循该框架进行能力评估和风险分级
- **前沿风险委员会（Frontier Risk Council）**: 将安全从业者和 OpenAI 团队联合评估前沿模型风险
- **Codex Security（原 Aardvark）**: OpenAI 代理安全研究工具，已发现 OpenSSH、GnuTLS、GOGS、Chromium 等项目的关键漏洞

### 与其他系统卡片
- **GPT-5 System Card**（2025-08-07）: 基线安全评估
- **GPT-5 System Card Addendum: Sensitive Conversations**（2025-10-27）: 首次引入心理健康和情感依赖评估
- **GPT-5.1 System Card Addendum**（2025-11-12）: 更新 Instant/Thinking 变体安全指标
- **GPT-5.3-Codex System Card**（2026-02-05）: 后续编码模型安全评估

### 第三方红队发现（SPLX Research）
- GPT-5 无系统提示时安全分仅 2.26（满分 100）
- 使用加固提示后提升至 55.40，但 GPT-4o 加固提示可达 94.40
- 说明系统提示加固对安全性至关重要

## 核心洞察

1. **双层监督是必要架构**: 面对 76% CTF 表现的模型，单层安全措施不足，需要模型级 + 系统级双重保障
2. **Trusted Access Controls 体现分级授权思维**: 不是一刀切禁止安全研究，而是通过身份验证的门控机制允许合法用例，这是安全能力开放的务实路径
3. **网络安全能力的双刃剑**: CTF 表现从 27% 到 76% 的飞跃意味着攻防能力同步提升，OpenAI 按"每个新模型都可能达到'高'级别"的假设来规划防控，体现了审慎态度
4. **提示注入仍是核心挑战**: 在代理编码场景中，模型需要访问外部代码和工具，提示注入风险被显著放大，受限模式与功能之间的平衡是关键设计决策
5. **安全基线持续改善但非线性**: 极端主义类别从 0.933 降至 0.925 说明安全改进不是单调递增的，需要在各类别间精细权衡

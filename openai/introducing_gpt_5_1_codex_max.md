# Introducing GPT-5.1-Codex-Max

## 基本信息
- **来源**: OpenAI Blog
- **发布日期**: 2025-11-19
- **链接**: https://openai.com/index/introducing-gpt-5-1-codex-max/
- **类别**: 模型发布 / 代码智能体

## 核心概述

GPT-5.1-Codex-Max 是 OpenAI 推出的前沿代理编码模型（Frontier Agentic Coding Model），基于 GPT-5.1 构建，专为高上下文、长时间跨度的软件工程任务设计。该模型的核心突破在于引入了 **上下文压缩技术（Context Compaction）**，使其成为首个能原生跨多个上下文窗口连贯工作的 AI 模型，以及新增的 **xhigh（超高）推理模式**，在 SWE-Bench Verified 上达到 77.9% 的准确率。

## 关键技术细节

### 1. 上下文压缩（Context Compaction）
- **核心机制**: 当对话或任务增长超出单个上下文窗口时，压缩机制自动识别关键信息、移除不必要的上下文，并用最关键的信息初始化新的上下文窗口
- **原生训练**: 不同于外挂式解决方案，Compaction 是原生训练过程——模型从零开始就被训练为能自主修剪历史记录，同时连贯保留最重要的上下文
- **处理规模**: 支持跨数百万 token 的单一任务连贯操作，突破传统上下文窗口限制
- **Token 效率**: 与 GPT-5.1-Codex 相比，推理 token 使用减少约 30%（SWE-Bench Verified 基准测试）

### 2. xhigh 推理模式（Extra-High Reasoning Effort）
- 支持可配置的推理努力等级，xhigh 为最高深度推理设置
- 在复杂任务上投入更多计算资源进行深度推理
- SWE-Bench Verified 在 xhigh 模式下达到 **77.9%** 准确率

### 3. 长期自主运行能力
- 支持多小时的自主代理操作（Multi-Hour Agentic Operation）
- 增强多文件项目支持
- 扩展编码循环能力
- Windows 环境兼容性

## 基准测试表现

### SWE-Bench Verified（2025 年 11 月）
| 模型 | 准确率 |
|---|---|
| Claude Opus 4.5 | 80.9% |
| **GPT-5.1-Codex-Max (xhigh)** | **77.9%** |
| Claude Sonnet 4.5 | 77.2% |
| GPT-5.1 | 76.3% |
| Gemini 3 Pro | 76.2% |
| Claude Opus 4.1 | 74.5% |

### Terminal-Bench 2.0
- GPT-5.1-Codex-Max 在 Terminal-Bench 上领先，达到 **58.1%**
- 后续 GPT-5.2 Codex CLI 进一步提升至 62.9%

### 网络安全 CTF
- 从 GPT-5（2025年8月）的 27% 提升至 GPT-5.1-Codex-Max 的 **76%**
- 是当时 OpenAI 部署的最强网络安全能力模型

## 可用性
- 初始对 ChatGPT Plus、Pro、Business、Edu 和 Enterprise 用户开放，作为默认 Codex 模型
- API 访问于 2025 年 12 月 11 日开放

## 已知问题
- 社区反馈指出指令遵循可靠性问题，包括模型忽略显式护栏和只读配置的情况
- 部分用户报告模型拒绝长期任务或将工作分割为 10-15 分钟短块

## 关联分析

### 与 GPT-5 系列演进
- **GPT-5**（2025-08-07）: 基础模型，建立推理能力基线
- **GPT-5.1**（2025-11-12）: 引入自适应推理（Adaptive Reasoning），Instant/Thinking 双变体
- **GPT-5.1-Codex-Max**（2025-11-19）: 引入 Compaction + xhigh，专攻长期编码任务
- **GPT-5.2**（2025-12-11）: 继承并改进 Codex-Max 能力
- **GPT-5.3-Codex**（2026-02-05）: 进一步迭代
- **GPT-5.4**（后续发布）: 最新版本

### 与 Codex 平台
- **Codex**（2025-05-16）: OpenAI 代理编码平台首次发布
- GPT-5.1-Codex-Max 成为 Codex 平台的默认模型，替代 GPT-5.1-Codex

### 竞品对比
| 工具 | 最佳场景 |
|---|---|
| **Codex-Max** | 跨百万 token 代码库的长期自主任务 |
| **Claude Code** | 更少代码变动（Less Code Churn） |
| **Cursor** | IDE 集成 |
| **Google Jules** | 免费层异步工作 |
| **Devin** | 浏览器访问 |

## 核心洞察

1. **Compaction 是架构级创新**: 不是简单的上下文管理或 RAG，而是原生训练模型自主管理上下文窗口，代表了 LLM 处理长任务的新范式
2. **从单次对话到持续工作流**: Codex-Max 标志着 AI 编码从"问答式辅助"向"持续自主工程"的转变，多小时自主操作是关键能力
3. **推理深度可配置化**: xhigh 推理模式体现了 OpenAI 对推理计算精细控制的方向，让用户在速度和深度之间做出选择
4. **安全性与能力的权衡**: CTF 表现从 27% 跃升至 76% 说明网络安全能力急剧提升，这同时带来双重用途（Dual-Use）风险
5. **Token 效率提升的实际意义**: 推理 token 减少 30% 直接降低 API 使用成本，对企业级部署有显著经济影响

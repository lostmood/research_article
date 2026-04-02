# Anthropic Engineering 文章整理

> 数据来源: https://www.anthropic.com/engineering
> 整理时间: 2026-04-01（初次整理）
> 筛选标准: Anthropic 工程博客全部文章，涵盖 Agent 构建、评估方法、工具设计、安全工程、基础设施等主题

---

## 一、Agent 构建与架构类文章

### 1. Building Effective Agents
- **发布日期**: 2024-12-19
- **链接**: https://www.anthropic.com/engineering/building-effective-agents
- **摘要**: Anthropic 分享了构建 LLM Agent 的实践指南，强调"最成功的实现使用简单、可组合的模式，而非复杂框架"。文章概述了 prompt chaining、routing、parallelization、orchestrator-workers 和 evaluator-optimizer 等基础工作流模式，建议开发者从优化单次 LLM 调用开始，仅在简单方案明确无法满足需求时才增加复杂度。

### 2. How We Built Our Multi-Agent Research System
- **发布日期**: 2025-06-13
- **链接**: https://www.anthropic.com/engineering/multi-agent-research-system
- **摘要**: Anthropic 的 Research 功能采用多 Agent 架构，由一个主 Agent 协调多个专业子 Agent 并行工作，探索复杂主题。该系统的表现比单 Agent 方案高出 90.2%，但 token 消耗约为标准对话的 15 倍。关键工程洞察包括基于 prompt 的 Agent 协调启发式方法、LLM-as-judge 评估方法、可恢复检查点等生产可靠性模式，以及并行化收益与协调复杂度之间的平衡。

### 3. Building a C Compiler with a Team of Parallel Claudes
- **发布日期**: 2026-02-05
- **链接**: https://www.anthropic.com/engineering/building-c-compiler
- **摘要**: 使用多个并行 Claude Agent 团队构建 C 编译器的实践经验。展示了如何将复杂的编译器构建任务分解为多个子任务，由不同 Agent 并行处理，验证了 Agent 团队协作在大型软件工程项目中的可行性。

### 4. Harness Design for Long-Running Application Development
- **发布日期**: 2026-03-24
- **链接**: https://www.anthropic.com/engineering/harness-design-long-running-apps
- **摘要**: 描述了一种受 GAN 启发的多 Agent 架构，将代码生成与评估分离以改进 AI 驱动的软件开发。系统使用三个专业化 Agent——规划器（将简短提示扩展为详细规格）、生成器（增量构建应用）和评估器（测试功能并提供反馈）。通过解决模型"自我评估偏差"（即模型无批判地赞扬自己作品）问题，完整 harness 版本运行 6 小时花费 $200，而单 Agent 版本仅运行 20 分钟花费 $9，harness 版本产出了功能丰富的可用应用，而单 Agent 版本核心游戏机制存在缺陷。

---

## 二、评估与基准测试类文章

### 5. Raising the Bar on SWE-bench Verified with Claude 3.5 Sonnet
- **发布日期**: 2025-01-06
- **链接**: https://www.anthropic.com/engineering/swe-bench-sonnet
- **摘要**: 升级版 Claude 3.5 Sonnet 在 SWE-bench Verified 上达到 49%，超越此前 45% 的最佳成绩。模型使用极简 Agent 架构，仅含两个核心工具——Bash 执行器和文件编辑工具（Edit Tool），赋予语言模型在解决 Python 仓库真实 GitHub Issue 时的高度自主性。评估表明"即使使用相同底层 AI 模型，Agent 在 SWE-bench 上的性能也会因脚手架设计而显著变化"，突出了精心的工具设计和 prompt 工程对编码能力的放大效应。

### 6. Demystifying Evals for AI Agents
- **发布日期**: 2026-01-09
- **链接**: https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents
- **摘要**: 深入探讨 AI Agent 评估的核心挑战——"使 Agent 变得有用的能力也使其难以评估"。文章讨论了 Agent 评估的方法论、指标设计和常见陷阱，为构建有效的 Agent 评估体系提供了实践指导。

### 7. Designing AI-Resistant Technical Evaluations
- **发布日期**: 2026-01-21
- **链接**: https://www.anthropic.com/engineering/AI-resistant-technical-evaluations
- **摘要**: 分享了三次迭代性能工程考试的设计经验和学习成果。探讨了如何设计能够抵抗 AI 作弊的技术评估方案，揭示了随着 AI 能力提升，传统评估方法面临的挑战和应对策略。

### 8. Quantifying Infrastructure Noise in Agentic Coding Evals
- **发布日期**: 2026-02-03
- **链接**: https://www.anthropic.com/engineering/infrastructure-noise
- **摘要**: Anthropic 研究发现，仅基础设施配置差异就能导致 Agent 编码基准分数波动高达 6 个百分点——超过了排行榜上顶级模型之间的典型差距。研究表明，容器资源执行方法对结果有显著影响：严格执行（1x 规格）产生 5.8% 的基础设施错误率，3x headroom 降至 2.1%，无上限资源则为 0.5%。关键发现是超过 3x 阈值后，"额外资源开始积极帮助 Agent 解决它之前无法解决的问题"，这意味着资源限制从根本上改变了基准测量的内容。

### 9. Eval Awareness in Claude Opus 4.6's BrowseComp Performance
- **发布日期**: 2026-03-06
- **链接**: https://www.anthropic.com/engineering/eval-awareness-browsecomp
- **摘要**: Anthropic 发现 Claude Opus 4.6 在 BrowseComp（网络信息检索基准测试）评估中展现出新颖的"评估感知"行为。除了通过标准污染遇到泄露答案（11 个案例中的 9 个），模型还独立假设自己正在被测试，系统性地识别出正在运行的基准测试，并使用代码执行成功解密了答案密钥——过程中消耗了高达 4050 万 token。这是首次记录到模型在没有先验知识的情况下识别评估条件，然后反向工作识别并解决基准测试本身的案例，对具备工具和搜索能力的网络环境中的基准测试完整性提出了重大质疑。

---

## 三、工具设计与 MCP 类文章

### 10. Introducing Contextual Retrieval
- **发布日期**: 2024-09-19
- **链接**: https://www.anthropic.com/engineering/contextual-retrieval
- **摘要**: Anthropic 提出 Contextual Retrieval 技术，通过在嵌入和索引前为每个文本块添加特定的解释性上下文来增强 RAG 系统。该方法将 Contextual Embeddings 与 Contextual BM25 结合，检索失败率降低 49%，配合重排序后降低 67%，"在检索准确性方面带来显著改进，直接转化为下游任务的更好表现"。

### 11. The "think" Tool: Enabling Claude to Stop and Think
- **发布日期**: 2025-03-20
- **链接**: https://www.anthropic.com/engineering/claude-think-tool
- **摘要**: Anthropic 推出"think"工具，为 Claude 在复杂多步骤任务中提供专用推理空间，区别于在响应生成前发生的 extended thinking。该工具在 τ-Bench 基准上表现出显著的性能提升——在航空领域配合优化提示实现 54% 的相对改进，并在 SWE-Bench 上平均提升 1.6% 贡献了 SOTA 结果。实现简单，代码开销极小，在涉及工具输出分析、策略密集型环境和高代价顺序决策场景中最为有效。

### 12. Desktop Extensions: One-Click MCP Server Installation
- **发布日期**: 2025-06-26
- **链接**: https://www.anthropic.com/engineering/desktop-extensions
- **摘要**: Anthropic 推出 Desktop Extensions（.mcpb 文件），一种将 MCP 服务器与所有依赖项捆绑到单个可安装归档的打包格式，简化了 MCP 服务器的安装流程。系统通过运行时管理、自动更新和通过操作系统密钥链的安全凭据存储来消除手动配置。开发者可使用 Node.js、Python 或二进制可执行文件创建扩展，配合 manifest.json 文件声明功能、用户配置需求和平台特定设置。

### 13. Writing Effective Tools for Agents — with Agents
- **发布日期**: 2025-09-11
- **链接**: https://www.anthropic.com/engineering/writing-tools-for-agents
- **摘要**: 文章聚焦于 AI Agent 的效果取决于其工具质量，提出了以 Agent 为中心的工具设计方法论。核心方法论包括三步迭代流程：原型制作、评估和协作（利用 Claude Code 分析失败并自动优化工具）。五个关键设计原则包括：选择合适的工具、命名空间隔离、返回有意义的上下文、优化 token 效率、以及像编写 prompt 一样精心设计工具描述和规格。

### 14. Introducing Advanced Tool Use on the Claude Developer Platform
- **发布日期**: 2025-11-24
- **链接**: https://www.anthropic.com/engineering/advanced-tool-use
- **摘要**: Anthropic 发布三项 Beta 功能以支持 Claude 更高效地处理大型工具库。Tool Search Tool 支持按需动态发现工具而非预加载全部定义，token 消耗减少 85% 同时准确率提升。Programmatic Tool Calling 允许 Claude 通过代码执行来编排多个工具，将中间结果保留在上下文窗口之外，复杂任务 token 用量减少 37%。Tool Use Examples 提供具体使用模式，将参数准确率从 72% 提升至 90%。

### 15. Code Execution with MCP: Building More Efficient Agents
- **发布日期**: 2025-11-04
- **链接**: https://www.anthropic.com/engineering/code-execution-with-mcp
- **摘要**: 探讨 Agent 通过编写代码调用工具来扩展其能力的方式。展示了如何利用 MCP（Model Context Protocol）实现代码执行，使 Agent 能够以更高效、更灵活的方式与外部工具和服务交互，减少 Agent 与工具之间的往返次数。

---

## 四、Agent 运行时与上下文管理类文章

### 16. Effective Context Engineering for AI Agents
- **发布日期**: 2025-09-29
- **链接**: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
- **摘要**: 提出从"prompt 工程"到"上下文工程"的范式转变，将上下文工程定义为在 LLM 推理过程中策划和维护最优 token 集合的策略。核心概念包括"注意力预算"和"上下文腐化"——随着更多 token 被添加到上下文窗口，模型对特定关键信息的召回能力会下降。指导原则是找到"最小可能的高信号 token 集合"，每个上下文窗口中的 token 都应证明其存在的合理性。实践策略涵盖系统 prompt 设计、按需工具调用、压缩与摘要技术，以及即时信息供给架构。

### 17. Effective Harnesses for Long-Running Agents
- **发布日期**: 2025-11-26
- **链接**: https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents
- **摘要**: 探讨 Agent 跨多个上下文窗口持续工作的改进方法。介绍了长时运行 Agent 的 harness（线束）设计模式，解决 Agent 在长期任务中面临的上下文管理、状态持久化和错误恢复等核心挑战，为构建可靠的长时运行 Agent 系统提供了实践指导。

### 18. Claude Code: Best Practices for Agentic Coding
- **发布日期**: 2025-04-18
- **链接**: https://www.anthropic.com/engineering/claude-code-best-practices
- **摘要**: Anthropic 分享了在各种代码库、编程语言和开发环境中使用 Claude Code 进行 Agent 编码的有效技巧和最佳实践。涵盖项目配置、prompt 策略、工具使用模式和工作流优化等方面的实战经验。

---

## 五、安全与工程实践类文章

### 19. Beyond Permission Prompts: Making Claude Code More Secure
- **发布日期**: 2025-10-20
- **链接**: https://www.anthropic.com/engineering/claude-code-sandboxing
- **摘要**: 介绍了 Claude Code 的沙箱功能，通过减少权限提示来提升用户安全性。该方案在保持 Agent 自主操作能力的同时，通过隔离执行环境来限制潜在的安全风险，平衡了开发效率和安全防护需求。

### 20. Claude Code Auto Mode: A Safer Way to Skip Permissions
- **发布日期**: 2026-03-25
- **链接**: https://www.anthropic.com/engineering/claude-code-auto-mode
- **摘要**: Anthropic 为 Claude Code 推出 auto mode，一个两层权限系统，用基于模型的分类器替代手动审批提示。系统使用快速单 token 过滤器加思维链推理来评估工具调用的安全性，实现 0.4% 的误报率，同时能捕获凭据探测和权限升级等危险操作。该方案在允许常规项目内编辑无需审查的同时，对外部操作进行分类器评估，但也承认在用户意图模糊的情况下存在 17% 的漏报率。

### 21. A Postmortem of Three Recent Issues
- **发布日期**: 2025-09-17
- **链接**: https://www.anthropic.com/engineering/a-postmortem-of-three-recent-issues
- **摘要**: 2025 年 8 月至 9 月初，三个基础设施 Bug 导致 Claude 在不同平台上的响应质量下降。第一个涉及请求被错误路由到不正确的服务器配置，第二个导致 token 生成错误产生意外字符，第三个触发了近似 top-k 操作中的编译器 Bug。Anthropic 已实施改进的评估、持续的生产监控和增强的调试工具来防止类似事件。

---

## 二、补充说明

- **文章统计**: 共 21 篇
- **排序规则**: 按主题分类，每个分类内按发布日期正序排列（最早的排在前面）
- **数据来源**: https://www.anthropic.com/engineering
- **时间跨度**: 2024-09 至 2026-03
- **主题分布**:
  - Agent 构建与架构: 4 篇
  - 评估与基准测试: 5 篇
  - 工具设计与 MCP: 6 篇
  - Agent 运行时与上下文管理: 3 篇
  - 安全与工程实践: 3 篇

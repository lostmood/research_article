# OpenAI Research & Safety 文章整理（AI技术相关）

> 数据来源: https://openai.com/research/index/
> 整理时间: 2026-04-01（初次整理）/ 2026-04-01（筛选重整）
> 筛选标准: 保留AI核心技术、模型发布、系统卡片、安全技术研究类文章，删除威胁运营报告和政策/运营类文章

---

## 一、Research（研究）类文章

### 1. Inside Our Approach to the Model Spec
- **发布日期**: 2026-03-25
- **链接**: https://openai.com/index/inside-our-approach-to-the-model-spec/
- **摘要**: OpenAI 深入介绍了 Model Spec 框架——定义模型行为的正式规范，包括指令冲突解决、用户自由尊重和安全优先级设定。核心组件"指令链"(Chain of Command) 为不同来源的指令分配权限级别，指导模型在冲突时如何优先处理。

### 2. Improving Instruction Hierarchy in Frontier LLMs
- **发布日期**: 2026-03-10
- **链接**: https://openai.com/index/improving-instruction-hierarchy/
- **摘要**: 引入 IH-Challenge 训练方法，迫使模型优先执行可信指令，增强"指令层级"，使模型对 prompt 注入攻击更具鲁棒性，提升面向安全边界的可调控性。

### 3. Introducing GPT-5.4 Thinking
- **发布日期**: 2026-03-05
- **链接**: https://deploymentsafety.openai.com/gpt-5-4-thinking
- **摘要**: GPT-5.4 系统卡片，该模型为 GPT-5 系列最新推理模型，针对专业工作、编码、计算机使用和工具搜索进行了优化，支持 1M token 上下文窗口，是首个实施高级网络安全风险缓解的通用模型。

### 4. Reasoning Models Struggle to Control Their Chains of Thought, and That's Good
- **发布日期**: 2026-03-05
- **链接**: https://openai.com/index/reasoning-models-cot-control/
- **摘要**: 引入 CoT-Control 研究，发现推理模型天然难以完美抑制或操纵自身的思维链，OpenAI 认为这是 AI 安全的积极属性，因为它增强了"可监控性"——使模型更难隐藏推理过程，便于安全系统观察和验证。

### 5. GPT-5.3 Instant System Card
- **发布日期**: 2026-03-02
- **链接**: https://openai.com/index/gpt-5-3-instant-system-card/
- **摘要**: GPT-5.3 Instant 的系统卡片，记录了该最新 Instant 模型在速度、上下文管理和网页搜索集成方面的改进及安全评估。

### 6. Why SWE-bench Verified No Longer Measures Frontier Coding Capabilities
- **发布日期**: 2026-02-23
- **链接**: https://openai.com/index/swe-bench-verified-analysis/
- **摘要**: OpenAI 分析认为 SWE-bench Verified 基准已因测试污染和测量失真而不再适合衡量前沿编码能力，建议改用 SWE-bench Pro 作为替代评估标准。

### 7. GPT-5.3-Codex System Card
- **发布日期**: 2026-02-05
- **链接**: https://openai.com/index/gpt-5-3-codex-system-card/
- **摘要**: GPT-5.3-Codex 的系统卡片，这是 OpenAI 首个在准备框架下被视为网络安全领域达到"高"能力阈值的模型发布，部署了专门的分层安全堆栈以阻止威胁行为者同时保持对合法网络防御人员的可用性。

### 8. Inside OpenAI's In-House Data Agent
- **发布日期**: 2026-01-29
- **链接**: https://openai.com/index/inside-our-in-house-data-agent/
- **摘要**: OpenAI 介绍了内部使用的 AI 数据智能体，由 GPT-5.2 和 Codex 驱动，帮助员工从超过 600 PB、约 70,000 个数据集的海量数据平台中快速提取洞察，支持 Slack、Web 和 IDE 等多种接入方式。

### 9. Introducing Prism
- **发布日期**: 2026-01-27
- **链接**: https://openai.com/index/introducing-prism/
- **摘要**: OpenAI 推出 Prism，一个免费的 LaTeX 原生科学写作和协作工作空间。集成 GPT-5.2，帮助研究人员撰写论文、管理引用、格式化公式和创建图表。

### 10. GPT-5.2-Codex System Card Addendum
- **发布日期**: 2025-12-18
- **链接**: https://openai.com/index/gpt-5-2-codex-system-card-addendum/
- **摘要**: GPT-5.2-Codex 的系统卡片补充文档，介绍了编码优化版本的专项安全措施，包括智能体沙箱和增强的网络安全防护，在准备框架下评估为网络安全领域"有能力"但未达到"高"能力阈值。

### 11. GPT-5.2 System Card
- **发布日期**: 2025-12-11
- **链接**: https://openai.com/index/gpt-5-2-system-card/
- **摘要**: GPT-5.2 的安全系统卡片，涵盖推理、工具使用和长上下文处理方面的改进评估，以及在准备框架下的安全评估结果。

### 12. Introducing GPT-5.2
- **发布日期**: 2025-12-11
- **链接**: https://openai.com/index/introducing-gpt-5-2/
- **摘要**: GPT-5.2 发布，包含 Instant、Thinking 和 Pro 三个变体，Thinking 版本引入可调节的"推理努力"参数，Pro 版本支持最多 400K token 上下文窗口和 xhigh 推理设置，在 AIME 2025（竞赛数学）上接近满分，在 SWE-Bench Pro 上创下新纪录。

### 13. Early Experiments in Accelerating Science with GPT-5
- **发布日期**: 2025-11-20
- **链接**: https://openai.com/index/accelerating-science-gpt-5/
- **摘要**: "OpenAI for Science"项目，探索 GPT-5 如何帮助数学、物理、生物和计算机科学领域的专家加速文献综述、实验设计、数据分析和证明生成等科研工作。

### 14. Introducing GPT-5.1-Codex-Max
- **发布日期**: 2025-11-19
- **链接**: https://openai.com/index/introducing-gpt-5-1-codex-max/
- **摘要**: GPT-5.1-Codex-Max 发布，专为高上下文、长时间跨度的软件工程任务设计，引入 compaction 技术实现跨多个上下文窗口的连贯操作，新增 xhigh 推理模式，在 SWE-Bench Verified 上达到 77.9% 准确率。

### 15. GPT-5.1-Codex-Max System Card
- **发布日期**: 2025-11-19
- **链接**: https://openai.com/index/gpt-5-1-codex-max-system-card/
- **摘要**: GPT-5.1-Codex-Max 的安全系统卡片，详细介绍了该智能体编码模型针对 prompt 注入和网络安全能力的安全缓解措施。

### 16. Introducing GPT-5.1
- **发布日期**: 2025-11-12
- **链接**: https://openai.com/index/introducing-gpt-5-1/
- **摘要**: GPT-5.1 发布，包含 Instant（低延迟对话优化）和 Thinking（复杂推理优化）两个变体，引入自适应推理能力，可根据问题复杂度自动调整计算投入，同时提升了指令遵循和对话温度。

### 17. GPT-5.1 Instant and Thinking System Card Addendum
- **发布日期**: 2025-11-12
- **链接**: https://openai.com/index/gpt-5-1-system-card-addendum/
- **摘要**: GPT-5.1 的系统卡片补充文档，更新了基线安全指标，扩展了心理健康和情感依赖的相关评估。

### 18. Sora 2 System Card
- **发布日期**: 2025-09-30
- **链接**: https://openai.com/index/sora-2-system-card/
- **摘要**: Sora 2 的安全系统卡片，介绍了迭代式部署策略，限制涉及照片级真实人物的图像上传，初始阻止所有视频上传，并对涉及未成年人的内容实施严格保护措施。

### 19. Introducing Sora 2
- **发布日期**: 2025-09-30
- **链接**: https://openai.com/index/introducing-sora-2/
- **摘要**: OpenAI 推出 Sora 2，新一代视频和音频生成模型，具备增强的物理准确性、真实感和可控性，支持同步对话和音效，通过 sora.com、iOS 应用和 API 提供服务。

### 20. GPT-5 System Card
- **发布日期**: 2025-08-07
- **链接**: https://openai.com/blog/gpt-5-system-card/
- **摘要**: GPT-5 系统卡片介绍了统一系统架构（快速模型 + 深度推理模型 + 实时路由器），以及"safe-completions"安全方法、"High"级别生物/化学能力分类等关键安全信息。

### 21. Introducing GPT-5 for Developers
- **发布日期**: 2025-08-07
- **链接**: https://openai.com/index/introducing-gpt-5-for-developers/
- **摘要**: OpenAI 向 API 开发者推出 GPT-5，该模型为统一系统架构，包含快速模型和深度推理模型，由实时路由器自动选择。具备高推理性能、新开发者控制功能和改进的编码任务表现。

### 22. Introducing ChatGPT Agent: Bridging Research and Action
- **发布日期**: 2025-07-17
- **链接**: https://openai.com/index/introducing-chatgpt-agent/
- **摘要**: 在 ChatGPT 中推出 Agent 模式，智能体能"思考并行动"，使用工具执行研究、预订、创建幻灯片等多步骤任务，在用户指导下自主完成复杂工作。

### 23. ChatGPT Agent System Card
- **发布日期**: 2025-07-17
- **链接**: https://openai.com/index/chatgpt-agent-system-card
- **摘要**: ChatGPT Agent 的系统安全卡片，记录了自主多步骤任务（网页导航、文件操作、服务集成等）的安全措施，包括 16 位 PhD 安全研究人员的红队测试。

### 24. Addendum: OpenAI o3 Operator
- **发布日期**: 2025-05-23
- **链接**: https://openai.com/index/o3-o4-mini-system-card-addendum-operator-o3/
- **摘要**: o3/o4-mini 系统卡片的补充文档，介绍了基于 o3 的 Operator 智能体模型（"计算机使用代理"），能够浏览网页和与 GUI 交互，替代此前基于 GPT-4o 的实现。

### 25. Introducing Codex
- **发布日期**: 2025-05-16
- **链接**: https://openai.com/index/introducing-codex/
- **摘要**: OpenAI 推出 Codex 智能体（研究预览版），一个基于云的自主软件工程智能体，运行在隔离的微型虚拟机中，由 Codex-1（o3 的软件开发微调版本）驱动，可自主完成代码编写、Bug 修复、测试运行等多任务，并引入 AGENTS.md 配置文件。

### 26. Introducing o3 and o4-mini
- **发布日期**: 2025-04-16
- **链接**: https://openai.com/index/introducing-o3-and-o4-mini/
- **摘要**: OpenAI 发布 o3 和 o4-mini 两个推理模型。o3 是最强大的推理模型，擅长编码、数学、科学和视觉任务；o4-mini 针对速度和成本效率优化。两者均支持增强的智能体工具调用能力（网页搜索、Python 执行、图像生成、视觉分析等）。

### 27. OpenAI o3 and o4-mini System Card
- **发布日期**: 2025-04-16
- **链接**: https://openai.com/index/o3-o4-mini-system-card/
- **摘要**: o3 和 o4-mini 模型的系统卡片，详细介绍了高级推理能力与完整工具使用的结合，以及通过大规模强化学习训练思维链的过程。

### 28. Natively Multimodal Image Generation
- **发布日期**: 2025-03-25
- **链接**: https://openai.com/index/introducing-4o-image-generation/
- **摘要**: OpenAI 发布原生多模态图像生成能力，将精确的、照片级真实感图像生成深度集成到模型生态系统中，支持文本渲染、风格控制和上下文理解。

### 29. Next-Generation Audio Models in the API
- **发布日期**: 2025-03-20
- **链接**: https://openai.com/index/next-gen-audio-models/
- **摘要**: OpenAI 在 API 中发布新一代音频模型，包括 gpt-4o-mini-tts（文本转语音）和 GPT-4o Transcribe/Mini Transcribe（语音转文本），支持可提示的语音交互，基于 Transformer 架构训练，显著提升多语言准确率和成本效率。

### 30. Introducing GPT-4.5
- **发布日期**: 2025-02-27
- **链接**: https://openai.com/index/introducing-gpt-4-5/
- **摘要**: OpenAI 发布 GPT-4.5（代号 "Orion"）研究预览版，通过大规模无监督学习提升世界知识广度，降低幻觉率，增强联想思维和情感智能，而非依赖推理链（CoT），是 GPT-4o 系列的重要升级。

### 31. GPT-4.5 System Card
- **发布日期**: 2025-02-27
- **链接**: https://openai.com/index/gpt-4-5-system-card/
- **摘要**: GPT-4.5 的安全系统卡片，安全顾问组评估为整体中等风险（CBRN 和说服力为中等风险，网络安全和模型自主性为低风险），未发现相比现有模型显著增加的安全风险。

### 32. Deep Research System Card
- **发布日期**: 2025-02-25
- **链接**: https://openai.com/research/deep-research-system-card
- **摘要**: Deep Research 的安全系统卡片，详细介绍了该智能体系统的安全测试、风险缓解（隐私、化学/生物威胁、违禁内容等）以及模型的网页浏览、文件解析和代码执行能力。

### 33. Introducing Deep Research
- **发布日期**: 2025-02-02
- **链接**: https://openai.com/index/introducing-deep-research/
- **摘要**: OpenAI 推出 Deep Research 功能，基于 o3 模型的早期版本，能够自主进行多步骤网络研究，浏览网页、解析文件并执行 Python 代码，帮助用户完成深度调研任务。

### 34. Introducing OpenAI o3-mini
- **发布日期**: 2025-01-31
- **链接**: https://openai.com/index/openai-o3-mini/
- **摘要**: OpenAI 正式推出 o3-mini 模型，一款高效推理模型，在保持较低成本的同时提供强大的编码、数学和科学推理能力。

### 35. OpenAI o3-mini System Card
- **发布日期**: 2025-01（与 o3-mini 发布同期）
- **链接**: https://openai.com/research/o3-mini-system-card
- **摘要**: o3-mini 模型的系统安全卡片，记录了该模型的能力评估、安全测试结果及风险缓解措施。

### 36. Introducing Operator
- **发布日期**: 2025-01-23
- **链接**: https://openai.com/index/introducing-operator/
- **摘要**: OpenAI 推出 Operator 研究预览版，这是一个能使用自己浏览器为用户执行任务的 AI 智能体，最初面向美国 Pro 用户开放。

---

## 二、Safety（安全）类文章

### 1. Open-Source Teen Safety Tools
- **发布日期**: 2026-03-25
- **链接**: https://openai.com/index/open-source-teen-safety-tools/
- **摘要**: OpenAI 开源发布一套工具，帮助开发者为青少年构建更安全的 AI 应用，作为更广泛的青少年安全倡议的一部分。

### 2. Creating with Sora Safely
- **发布日期**: 2026-03-23
- **链接**: https://openai.com/index/creating-with-sora-safely/
- **摘要**: 介绍如何安全地使用 Sora 进行视频创作，包括安全使用指南、内容审核措施和防止滥用的保护机制。

### 3. How We Monitor Internal Coding Agents for Misalignment
- **发布日期**: 2026-03-19
- **链接**: https://openai.com/index/how-we-monitor-internal-coding-agents-misalignment/
- **摘要**: OpenAI 介绍了使用 GPT-5.4 Thinking 作为低延迟监控系统，监控内部编码智能体的完整对话历史（包括思维链 CoT），检测不符合用户意图或违反安全策略的行为（如 base64 编码命令绕过、未授权网络访问等），并在 30 分钟内升级高严重性案例。

### 4. GPT-5.4 Thinking System Card
- **发布日期**: 2026-03-05
- **链接**: https://deploymentsafety.openai.com/gpt-5-4-thinking
- **摘要**: GPT-5.4 Thinking 的安全系统卡片，该模型是 GPT-5 系列中首个针对高能力网络安全风险实施专项缓解措施的通用模型，在 GPT-5.3-Codex 安全方法基础上进一步扩展。

### 5. Advancing Independent Research on AI Alignment
- **发布日期**: 2026-02-19
- **链接**: https://openai.com/index/advancing-independent-research-ai-alignment/
- **摘要**: OpenAI 宣布投入 750 万美元资助"The Alignment Project"，推进独立 AI 对齐研究，支持外部研究人员开展对齐安全相关的独立研究工作。

### 6. Keeping Your Data Safe When an AI Agent Clicks a Link
- **发布日期**: 2026-01-28
- **链接**: https://openai.com/index/ai-agent-link-safety
- **摘要**: 介绍 AI 智能体在浏览网页和点击链接时的数据安全保护措施，针对 prompt 注入攻击和其他安全威胁提供防护指导。

### 7. Introducing gpt-oss-safeguard
- **发布日期**: 2025-10-29
- **链接**: https://openai.com/index/introducing-gpt-oss-safeguard
- **摘要**: 推出 gpt-oss-safeguard 开源权重推理模型（20B 和 120B 参数版本），专为安全分类任务设计。开发者可输入自定义策略，模型通过推理能力解释策略并进行内容分类，提供结构化的推理过程和分类结果。

### 8. gpt-oss-safeguard Technical Report
- **发布日期**: 2025-10-29
- **链接**: https://openai.com/index/gpt-oss-safeguard-technical-report/
- **摘要**: gpt-oss-safeguard 的技术报告，详细介绍了模型从 gpt-oss 基础模型进行后训练的过程，以及在安全分类、内容审核和思维链监控等方面的技术细节。

### 9. Working with US CAISI and UK AISI to Build More Secure AI Systems
- **发布日期**: 2025-09（约）
- **链接**: https://openai.com/index/us-caisi-uk-aisi-ai-update/
- **摘要**: OpenAI 与美国 AI 标准与创新中心 (CAISI) 和英国 AI 安全研究所 (UK AISI) 合作进行结构化安全评估，包括对 GPT-5.3-Codex 和 ChatGPT 智能体系统的红队测试、生物安全防护和智能体系统安全评估等。

### 10. Findings from a Pilot Anthropic–OpenAI Alignment Evaluation Exercise: OpenAI Safety Tests
- **发布日期**: 2025-08-27
- **链接**: https://openai.com/index/openai-anthropic-safety-evaluation/
- **摘要**: OpenAI 和 Anthropic 首次联合对齐评估合作，双方使用各自的内部安全和错位测试方法论互相测试已发布模型。发现系统性谄媚(sycophancy)是普遍问题，o3 推理模型在多个评估场景中表现出较强鲁棒性。

### 11. From Hard Refusals to Safe-Completions: Toward Output-Centric Safety Training
- **发布日期**: 2025-08（与 GPT-5 同期发布，arXiv:2508.09224）
- **链接**: https://openai.com/index/gpt-5-safe-completions/
- **摘要**: 提出"safe-completions"方法，从传统的硬拒绝转向以输出为中心的安全训练。通过关注模型输出本身的安全性（而非二元分类用户意图），在保持高可用性的同时严格遵守安全策略约束，特别擅长处理"双重用途"场景。

### 12. Our Updated Preparedness Framework
- **发布日期**: 2025-04-15
- **链接**: https://openai.com/index/updating-our-preparedness-framework/
- **摘要**: OpenAI 发布更新版"准备框架"(Preparedness Framework)，这是自 2023 年 12 月首版以来的首次重大更新，为前沿模型的风险评估和安全决策提供系统化的方法论。

### 13. Operator System Card
- **发布日期**: 2025-01-23
- **链接**: https://openai.com/index/operator-system-card/
- **摘要**: Operator 的安全系统卡片，详细介绍了针对 prompt 注入和越狱的多层防护方案，以及隐私保护、安全措施和外部红队测试等内容。

### 14. Deliberative Alignment: Reasoning Enables Safer Language Models
- **发布日期**: 2024-12-20
- **链接**: https://openai.com/index/deliberative-alignment/
- **摘要**: 提出"审慎对齐"策略，教导模型（特别是 o1 系列）学习安全规范并对其进行推理，而非仅依赖预训练行为，通过推理能力实现更安全的语言模型。

---

## 三、补充说明

- **筛选标准**: 保留AI核心技术（模型发布、系统卡片、技术研究、安全技术方法论）相关文章，删除威胁运营报告（Disrupting Malicious Uses 系列4篇）和政策/运营类文章（青少年安全政策、Bug Bounty、基金会等8篇），共删除12篇
- **文章统计**: Research 36篇 + Safety 14篇 = 共 50 篇
- **排序规则**: 每个分类内按发布日期倒序排列（最新的排在前面）
- **数据来源**: https://openai.com/research/index/ 及 https://deploymentsafety.openai.com/
- **时间跨度**: 2024-12 至 2026-03
- 部分日期为近似值（标注"约"），因搜索结果未提供精确日期
- 部分文章同时涉及 Research 和 Safety 两个类别（如 System Card 类文档），已根据主要侧重点进行分类

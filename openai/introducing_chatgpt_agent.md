# Introducing ChatGPT Agent: Bridging Research and Action — 统一智能体模式

> 来源: https://openai.com/index/introducing-chatgpt-agent/
> 发布日期: 2025-07-17
> 类别: Research - 产品发布 / 智能体系统

---

## 一、核心概述

OpenAI 于 2025 年 7 月 17 日在 ChatGPT 中推出 **Agent 模式**（Agent Mode），这是一个统一的智能体系统，能够**"思考并行动"**（think and act），将此前分散的多种能力整合为单一智能体体验。Agent 模式融合了 **Operator 的远程浏览器操控能力**、**Deep Research 的网络信息综合能力**，以及终端执行、API 调用等工具，使 ChatGPT 能够在自己的**虚拟计算机**（virtual computer）上独立完成复杂的多步骤任务。

> "ChatGPT Agent bridges research and action — a unified agentic system combining Operator's browser, Deep Research's synthesis, terminal, API access, and app connectors."

---

## 二、关键技术细节

### 2.1 工具集（Tool Suite）

ChatGPT Agent 配备了五类核心工具：

| 工具 | 功能描述 |
|------|----------|
| **Visual Browser（可视化浏览器）** | 基于 GUI 的网页交互，通过远程浏览器（代号 Atlas）操控网页 |
| **Text-based Browser（文本浏览器）** | 基于推理的网络查询，用于信息检索和综合 |
| **Terminal（终端）** | 命令行执行能力，支持代码运行和系统操作 |
| **Direct API Access（直接 API 访问）** | 程序化调用外部服务 |
| **ChatGPT Connectors（应用连接器）** | Gmail、GitHub 等第三方应用集成，安全访问用户数据 |

### 2.2 核心能力

- **多步骤任务执行**: 研究、预订餐厅/旅行、创建演示文稿/幻灯片、更新电子表格
- **虚拟计算机**: 在 OpenAI 管理的远程环境中独立运行，浏览网页并与网站交互
- **自主规划与执行**: 接收高层级指令后自行分解任务、选择工具、迭代执行
- **数据分析**: 数据处理、对比分析、信息综合

### 2.3 安全与评估

- **Preparedness Framework 评级**: 被分类为**生物和化学能力"高"（High）**等级，即使未发现明确的武器化证据，也作为预防措施激活了相应安全保障
- **BrowseComp 基准**: 用于评估浏览智能体定位难找信息的能力——问题"难以回答但易于验证"，答案唯一且简短
  - GPT-4o 和 GPT-4.5 表现不佳
  - Deep Research 智能体解决了超过一半的问题
  - 性能随推理时计算（inference-time compute）扩展
- **配套发布安全系统卡片**（System Card），详细记录风险评估和缓解措施

### 2.4 可用性

| 套餐 | Agent 模式 |
|------|-----------|
| **ChatGPT Plus** | 可用 |
| **ChatGPT Pro** | 最大化使用额度，包含无限消息和上传 |

---

## 三、关联分析

### 与 Operator 的演进关系

ChatGPT Agent 是 2025 年 1 月推出的 **Operator** 产品的自然演进。Operator 提供了独立的远程浏览器操控界面，而 Agent 模式将这一能力**内化到 ChatGPT 主界面**中，实现了"一个入口，所有能力"的统一体验。Operator 的底层模型也经历了从 GPT-4o 到 **o3**（2025-05-23 Addendum）的升级。

### 与 Deep Research 的融合

Agent 模式将 Deep Research 的信息综合能力与 Operator 的操作执行能力**合二为一**。此前用户需在"研究"和"行动"之间手动切换，现在智能体可以在同一会话中先研究、再执行。

### 与 o3/o4-mini 系统卡片的关联

Agent 模式的底层推理能力受益于 **o3**（2025-04-16）及其后续模型的安全训练。o3 Operator Addendum（2025-05-23）中建立的安全措施（Prompt Injection Monitor、Watch Mode 等）为 ChatGPT Agent 的安全框架奠定了基础。

### 与 GPT-5.4 mini/nano 子代理时代的关联

ChatGPT Agent 是"子代理时代"的前奏。2026 年 3 月发布的 **GPT-5.4 mini 和 nano** 为多代理架构提供了经济高效的计算基础，使得 Agent 模式可以将不同复杂度的子任务委托给不同规模的模型。

### 与 Codex 的区分

**Codex**（2025-05-16）专注于软件工程领域的自主编码，运行在隔离微型虚拟机中；而 ChatGPT Agent 是**通用型**智能体，覆盖网页浏览、信息研究、日常任务等更广泛场景。两者共同构成 OpenAI 智能体产品矩阵的不同维度。

### 与 Monitor Internal Coding Agents 的关联

OpenAI 于 2026 年 3 月发布的内部编码智能体监控研究，为自主智能体的安全运行提供了方法论。ChatGPT Agent 作为面向消费者的自主智能体，其安全保障体系借鉴了内部智能体监控的经验。

---

## 四、核心洞察

1. **统一入口的战略意义**: Agent 模式将 Operator（操作）、Deep Research（研究）、Connectors（数据）整合为一，这是从"工具集合"到"统一智能体"的关键跨越——用户不再需要选择使用哪个产品
2. **"高"生物化学风险评级的预防逻辑**: OpenAI 在没有明确证据的情况下主动将模型评为"高"风险并激活保障措施，反映了对自主智能体（能联网、能执行）的谨慎态度
3. **BrowseComp 推理时计算扩展**: 浏览智能体的性能随推理时计算扩展，与数学推理（AIME）和编码任务中观察到的 scaling law 一致，表明智能体任务也遵循类似的扩展规律
4. **从"对话"到"代理"的产品转型**: ChatGPT 从对话式 AI 演变为能够代替用户行动的智能体，标志着 LLM 产品形态的根本转变
5. **Connectors 生态的护城河效应**: Gmail、GitHub 等应用连接器创建了数据和工作流锁定效应，使智能体能力与用户生态深度绑定

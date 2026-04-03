# Introducing Codex — 基于云的自主软件工程智能体

> 来源: https://openai.com/index/introducing-codex/
> 发布日期: 2025-05-16
> 类别: Research - 产品发布 / 软件工程智能体

---

## 一、核心概述

OpenAI 于 2025 年 5 月 16 日发布 **Codex**（研究预览版），这是一个**基于云的自主软件工程智能体**（cloud-based software engineering agent），运行在安全的**隔离微型虚拟机**（sandboxed micro virtual machine, microVM）中。Codex 由 **codex-1** 驱动——一个基于 **o3 微调（fine-tuned）的软件开发专用模型**，具备**自愈能力**（self-healing capability），能够迭代修复代码直至测试通过。Codex 还引入了 **AGENTS.md** 配置文件概念，让 AI 智能体能够理解项目特定的约定和工作流。

> "Codex is a cloud-based autonomous software engineering agent powered by codex-1 (o3 fine-tuned for software development), running in isolated microVMs with self-healing capability and AGENTS.md project configuration."

---

## 二、关键技术细节

### 2.1 codex-1 模型

- **基础模型**: 基于 **o3** 微调
- **专注领域**: 软件工程任务优化
- **核心特性**: 自愈能力——检测到测试失败后自动迭代修复
- **继任版本**: 后续演进为 gpt-5.2-codex → GPT-5.3-Codex
- **SWE-bench 表现**: 与 Claude Opus、Gemini Flash、DeepSeek v3.2 Reasoner 等前沿模型竞争

### 2.2 沙箱微型虚拟机架构

| 特性 | 描述 |
|------|------|
| **隔离环境** | 每个任务运行在独立的 microVM 中 |
| **预加载** | 自动加载用户的代码库和开发环境配置 |
| **安全性** | 完全沙箱化，防止对外部系统的未授权访问 |
| **并行执行** | 支持**多任务并行处理**，多个编码任务同时运行 |

### 2.3 AGENTS.md 配置文件

**AGENTS.md** 是一种全新的项目配置概念——类似于 README.md 但面向 AI 智能体而非人类：

- **定位**: "README.md for AI agents"
- **内容**: 代码库上下文、编码约定、风格实践、工作流指引
- **作用**: 让 Codex 适应不同代码库的特定要求
- **放置位置**: 仓库根目录或子目录
- **影响力**: 后续被广泛采用，成为 AI 编码智能体的行业惯例

### 2.4 核心能力

- **代码编写**: 根据自然语言指令生成代码
- **调试修复**: 定位并修复 Bug
- **测试生成**: 自动编写测试代码
- **Pull Request 生成**: 自动创建 PR，模拟真实的代码提交工作流
- **自然语言交互**: 接受"添加新功能"、"修复这个 Bug"、"编写测试代码"等自然语言指令

### 2.5 自愈能力（Self-Healing Capability）

Codex-1 的**自愈工作流**：

```
接收任务指令
    ↓
生成代码实现
    ↓
运行测试套件
    ↓
检测到失败? ──是──→ 分析错误原因
    │                    ↓
    否                修复代码
    ↓                    ↓
完成并提交          重新运行测试
                        ↓
                    （循环直到通过）
```

这种自愈能力使 Codex 不仅能生成代码，还能**对代码质量负责**——类似于经验丰富的开发者在提交 PR 前确保所有测试通过。

### 2.6 可用性

- **目标用户**: ChatGPT Pro、Team、Enterprise 用户
- **接入方式**: 集成在 ChatGPT 界面中
- **发布状态**: 研究预览（Research Preview）

---

## 三、关联分析

### 与 o3/o4-mini 的模型关系

Codex-1 直接基于 **o3** 微调，继承了 o3 的推理能力并针对软件工程场景优化。o3（2025-04-16 发布）的强大推理链为代码理解、Bug 诊断和多步修复提供了基础能力。OpenAI 后续还发布了专门的 **o3/o4-mini Codex System Card Addendum**，详细记录了 Codex 场景下的安全评估。

### 与 o3 Operator Addendum 的同期关系

Codex（2025-05-16）和 [o3 Operator Addendum](o3_operator_addendum.md)（2025-05-23）仅间隔一周发布。两者都基于 o3 系列但面向不同领域：
- **Codex**: 软件工程（代码生成、测试、PR）
- **Operator**: 网页浏览和 GUI 操作

这一并行发布展示了 o3 作为"智能体基础模型"的多场景适用性。

### 与 Codex Figma 集成的演进

[Codex Figma](codex_figma_design_code_integration.md)（2026-02-26）将 Codex 从"纯编码工具"扩展为**设计-代码协作平台**。到那时，Codex 的底层模型已演进到 **GPT-5.3-Codex**（比初始版快 25%），桌面应用也增加了 macOS 原生应用、CLI、IDE 扩展、Web 四种接入方式。

### 与 GPT-5.4 mini/nano 子代理时代的关联

[GPT-5.4 mini/nano](gpt_5_4_mini_nano_subagent_era.md)（2026-03-17）中，mini 在 Codex 中仅使用 30% 配额，使得低推理强度的编码子任务可以委托给更经济的模型。这体现了 Codex 架构从"单一大模型"向"多模型协作"的演进。

### 与 ChatGPT Agent 的区分

[ChatGPT Agent](introducing_chatgpt_agent.md)（2025-07-17）是**通用型智能体**，覆盖网页浏览、信息研究、日常任务；Codex 是**垂直型智能体**，专注于软件工程。两者的共同点是都运行在远程/云端环境中，都具备自主多步骤执行能力。

### 与 Monitor Internal Coding Agents 的关联

OpenAI 于 2026 年 3 月发布的**内部编码智能体监控**研究，直接关联到 Codex 等编码智能体的安全运行。该研究提供的监控方法论（行为日志分析、异常检测）为 Codex 的安全保障体系提供了理论支撑。

### AGENTS.md 的行业影响

AGENTS.md 的概念被 **Anthropic Claude Code**（使用 CLAUDE.md）等竞品迅速借鉴和扩展，成为 AI 编码智能体与代码库交互的标准化接口。这体现了 OpenAI 在产品创新上的引领作用。

---

## 四、核心洞察

1. **"AI 作为软件工程师"的产品化**: Codex 不是代码补全工具（如 Copilot），而是能够独立完成从理解需求到提交 PR 的完整工作流的**自主智能体**——这是从"辅助"到"代理"的质变
2. **microVM 沙箱的安全-自由度平衡**: 隔离的微型虚拟机让 Codex 拥有完整的开发环境自由度（安装依赖、运行测试、执行命令），同时通过沙箱化确保安全——这种架构为自主编码智能体设定了行业标准
3. **自愈能力的工程哲学**: "迭代修复直至测试通过"模拟了资深开发者的工作方式——不是一次性生成完美代码，而是通过持续测试和修复达到质量标准
4. **AGENTS.md 作为 AI-代码库接口标准**: 这一简单但影响深远的创新，定义了 AI 智能体理解和适应代码库的标准化方式，类似于 .gitignore 定义了版本控制的忽略规则
5. **并行任务执行的生产力倍增**: 多个编码任务在独立 microVM 中并行运行，使一个工程师可以同时推进多个功能开发——这是"一个工程师的产出 = 十个工程师"的技术基础

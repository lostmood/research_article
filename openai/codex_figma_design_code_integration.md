# OpenAI Codex and Figma Partnership — 无缝的代码到设计工作流

> 来源: https://openai.com/index/figma-partnership/
> 发布日期: 2026-02-26
> 类别: Research - 产品与工具集成

---

## 一、核心概述

OpenAI 与 Figma 于 2026 年 2 月 26 日宣布战略合作伙伴关系，通过 Figma 的 **MCP（Model Context Protocol）服务器** 将 OpenAI 的 Codex AI 编码助手直接集成到 Figma 平台中，实现**无缝的代码到设计双向工作流**（seamless code-to-design workflow）。

> "OpenAI Codex and Figma launch seamless code-to-design collaboration."

---

## 二、Codex 桌面应用（macOS）

### 应用形态

OpenAI 于 2026 年 2 月 2 日发布了 **Codex 桌面应用（macOS）**，作为管理多个 AI 编码代理的"指挥中心"（command center）。

**多种接入方式：**
- **桌面应用** — macOS 原生应用，全屏 CLI UI
- **CLI（命令行）** — 完整终端 UI，支持存储库读写
- **IDE 扩展** — VS Code、Cursor、Windsurf 支持
- **Web 界面** — Codex Cloud 用于云端任务委托

### 核心功能
- 会话管理（`codex resume` 恢复最近会话）
- 快速提示模式（单次查询）
- 三种操作模式：**自动模式**、**只读模式**、**受限模式**
- 按 Enter 注入新指令，Tab 排队后续提示
- 驱动模型：**GPT-5.3-Codex**

---

## 三、Figma MCP 服务器集成

### 技术架构

Figma MCP 服务器充当桥梁（bridge），允许 Codex 以结构化方式访问 Figma 的设计上下文。

- **远程服务器 URL**: `https://mcp.figma.com/mcp`
- **传输协议**: 支持 StandardIO（本地进程通信）和 HTTP（远程连接）

### 安装步骤

1. 在 Codex 中进入 "Settings → MCP Servers"
2. 创建新的 MCP 服务器
3. 配置 Figma 个人访问令牌（Personal Access Token）
4. 登录 Figma 账户
5. 获取 Figma 设计链接并在 Codex 中使用

### 关键工具（MCP Tools）

| 工具名称 | 功能 |
|---------|------|
| `get_design_context` | 从 Figma 提取关键设计信息 |
| `generate_figma_design` | 生成 Figma 设计文件 |
| `get_variable_defs` | 检索变量定义 |
| `get_code_connect_map` | 将 Figma 节点映射到代码组件 |
| `get_code_connect_suggestions` | AI 驱动的映射建议 |
| `add_code_connect_map` | 映射 Figma 元素到 React 等框架实现 |
| `get_screenshot` | 捕获选区屏幕截图 |
| `create_design_system_rules` | 创建自定义设计系统规则 |

---

## 四、双向代码-设计工作流

### 设计转代码（Design → Code）

1. 设计师在 Figma 中创建设计
2. Codex 通过 MCP 服务器获取设计上下文（框架、位置、颜色、变体、资源）
3. 自动生成使用真实 React 组件、属性和变体的 UI 代码

### 代码返回设计（Code → Design）

1. 运行的 UI 实现可以返回到 Figma 画布
2. 进行进一步的设计优化和迭代
3. 创建**持续的反馈循环**（continuous feedback loop）

### 核心能力
- **消除手动翻译**: 消除设计系统与开发环境之间的手动转换需求
- **设计系统集成**: 支持组件、变量、样式
- **Playwright Interactive**: 支持基于浏览器的比较和迭代
- **Code Connect**: 将已发布的 Figma 组件映射到源文件

---

## 五、GPT-5.3-Codex 模型

- **发布时间**: 2026 年 2 月 5 日
- **性能提升**: 比 GPT-5.2-Codex **快 25%**
- **基准表现**: SWE-Bench Pro 和 Terminal-Bench 2.0 名列前茅
- **安全评级**: 首个在准备框架下被视为网络安全领域达到 **"高"（High）** 能力阈值的模型
- **Codex-Spark 变体**: 超过 **1,000 tokens/秒** 的近即时编码，专为实时反馈设计

---

## 六、与 Anthropic/Claude Code Figma 集成对比

Figma 先与 Anthropic 合作（2026-02-17），后与 OpenAI 合作（2026-02-26），两者间隔仅 9 天。

| 维度 | OpenAI Codex | Anthropic Claude Code |
|------|-------------|----------------------|
| **执行环境** | OpenAI 管理的云容器 | 本地终端/环境 |
| **Agent 模式** | 平行智能体独立运行 | Agent Teams 共享任务列表 |
| **Token 效率** | 更高效（更少 token） | 约 4× token 使用 |
| **上下文** | 标准上下文 | 1M token 上下文 |
| **Figma 工具** | MCP 服务器集成 | `use_figma` 工具 via MCP |
| **特色功能** | 独立 Figma 文件写入 | 创建组件、修复 Auto Layout |

### 工作流推荐
- **设计到代码**: Claude Code with Opus 在像素完美生成方面表现良好
- **快速原型**: Codex 在明确定义的执行任务中表现优异
- **混合方案**: Codex 快速原型 + Claude Code Agent Teams 代码审查和重构

---

## 七、MCP 协议技术要点

### 协议基础
- **创建者**: Anthropic 创建的开源标准
- **基础**: JSON-RPC 2.0
- **灵感**: Language Server Protocol（LSP）
- **验证**: JSON Schema（Draft 2020-12）

### 核心能力
1. **Resources（资源）** — 提供上下文和数据
2. **Tools（工具）** — 可执行函数
3. **Prompts（提示）** — AI 交互模板
4. **Elicitation（引发）** — 服务器发起的信息请求

### 安全要求
- 宿主必须在暴露用户数据前获得明确用户同意
- 宿主必须在调用工具前获得明确用户同意
- 所有资源 URI 需要适当验证

---

## 八、关联分析

### 与 OpenAI Codex 发布的关联

此合作建立在 2025 年 5 月发布的 **Introducing Codex** 基础之上——那时 Codex 作为基于云的自主软件工程智能体首次亮相，引入了 **AGENTS.md** 配置文件概念。Figma 集成将 Codex 从"纯编码工具"扩展为**设计-代码协作平台**。

### 与 GPT-5.3-Codex System Card 的关联

**GPT-5.3-Codex System Card**（2026-02-05）指出该模型是首个达到网络安全"高"能力阈值的模型。Figma 集成在利用这种强大编码能力的同时，也需要遵循系统卡片中记录的安全措施。

### 与 OpenAI Data Agent 的关联

**Inside OpenAI's In-House Data Agent**（2026-01-29）描述了 OpenAI 内部使用的 AI 数据智能体支持 Slack、Web 和 IDE 等多种接入方式。Codex 桌面应用 + Figma MCP 集成延续了相同理念——**AI 智能体通过多种接口融入现有工作流**。

### 与 MCP 生态的行业意义

值得注意的是，MCP 协议由 **Anthropic 创建**，而 OpenAI 的 Codex 在此使用 Anthropic 创建的标准来集成 Figma。这体现了 AI 行业在**基础设施标准**层面的趋同——即使在模型层面竞争，工具接口层面趋向统一标准。

---

## 九、核心洞察

1. **AI 开发工具的平台化**: Codex 从命令行工具进化为跨设计-代码的协作平台
2. **MCP 成为行业标准**: OpenAI 采用 Anthropic 创建的 MCP 协议，标志着 AI 工具接口标准的统一
3. **设计-代码边界模糊化**: 双向工作流使"设计师"和"开发者"的角色界限进一步模糊
4. **竞合格局**: Figma 同时与 OpenAI 和 Anthropic 合作，平台方通过多供应商策略最大化价值
5. **开发者体验为王**: 桌面应用、CLI、IDE 扩展、Web 四种接入方式体现了对开发者体验的极致追求

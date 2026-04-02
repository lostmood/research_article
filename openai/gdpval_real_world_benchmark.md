# GDPval: Measuring the Performance of Our Models on Real-World Tasks

> 来源: https://openai.com/index/gdpval/
> 论文: arXiv:2510.04374 (2025-10-05)
> 公开发布: ~2026-03-05（与 GPT-5.4 同步）
> 类别: Research - 评估基准

---

## 一、核心概述

**GDPval**（Gross Domestic Product validation）是 OpenAI 开发的新型评估框架，用于衡量 AI 模型在**真实经济价值相关的工作任务**上的表现。它代表了 AI 评估从学术基准向经济导向基准的范式转变（paradigm shift）。

> "GDPval measures AI performance on economically valuable, real-world tasks across 44 occupations in 9 major industries."

---

## 二、方法论

### 2.1 数据集设计

- **完整数据集**: 1,320 个经过充分审核的任务
- **每个职业**: 30 个任务
- **职业数量**: 44 个
- **行业覆盖**: 9 个美国 GDP 主要贡献行业
- **薪酬总额**: 44 个职业的年薪酬总和约 **$3 万亿**，占美国劳动收入的约 25%

### 2.2 任务设计者

- 由各领域 **平均 14 年以上工作经验** 的专业人士创建和审核（最少 4 年）
- 任务基于**实际工作交付物**（real-world deliverables）：
  - 法律摘要、工程蓝图、护理计划
  - 社交媒体文章、电子表格、幻灯片演示
  - 财务分析、代码审查等

### 2.3 数据来源

- 美国劳动统计局（BLS）
- 劳动部门 O*NET 工作活动数据库

### 2.4 开源"黄金集"（Gold Set）

- **220 个任务**（每个职业 5 个，5 × 44 = 220）
- 已在 Hugging Face 开源：`openai/gdpval`
- 安装：`pip install inspect-evals[gdpval]`
- 运行：`uv run inspect eval inspect_evals/gdpval --model openai/gpt-5-nano`

---

## 三、基准演进对比

| 阶段 | 基准 | 特点 |
|------|------|------|
| 经典学术 | MMLU | 多学科考试风格；已饱和（~99%） |
| 应用评估 | SWE-Bench | 软件工程 bug 修复 |
| 应用评估 | MLE-Bench | 机器学习工程 |
| 应用评估 | Paper-Bench | 科学推理 |
| 市场评估 | SWE-Lancer | 基于真实薪酬的自由职业软件工程 |
| **经济评估** | **GDPval** | **基于真实经济价值的 44 职业知识工作** |

---

## 四、模型性能结果

### 整体结果

| 模型 | GDPval 得分 | 说明 |
|------|------------|------|
| **GPT-5.4** | **83.0%** | 匹配或超越行业中期专业人士 |
| GPT-5.2 | 70.9% | 前代旗舰 |
| 提升幅度 | +12.1% | - |

### 按职业的 AI 胜率（部分）

| 排名 | 职业 | AI 胜率 |
|------|------|---------|
| 1 | 柜台与租赁店员 | 81% |
| 2 | 销售经理 | 79% |
| 3 | 运输与库存店员 | 76% |
| 4 | 编辑 | 75% |
| 5 | 软件开发人员 | 70% |
| ... | ... | ... |
| 42 | 机械工程师 | 23% |
| 43 | 工业工程师 | 17% |
| 44 | 电影与视频编辑 | 17% |

### 关键发现

- AI 完成任务速度**约 100 倍快**，成本**约 100 倍便宜**
- 但 **29% 的 AI 输出**需要重大修正或无法使用
- **3% 的 AI 输出**包含可能灾难性的错误
- 与人类监督结合时，显示 **1.2-1.6 倍的成本节省潜力**

---

## 五、论文信息

- **标题**: GDPval: Evaluating AI Model Performance on Real-World Economically Valuable Tasks
- **arXiv ID**: 2510.04374
- **发布日期**: 2025-10-05
- **许可证**: CC BY 4.0
- **作者团队**: 40+ 位 OpenAI 研究人员（Tejal Patwardhan, Rachel Dias, Alex Tamkin, Miles McCain 等）

---

## 六、关联分析

### 与 SWE-Bench Verified 的关联

OpenAI 此前发表文章认为 SWE-Bench Verified 因测试污染和测量失真已不再适合衡量前沿编码能力，建议改用 SWE-bench Pro。GDPval 的出现进一步推动了这一趋势——从单一领域基准转向**跨职业、经济导向**的综合评估。

### 与 GPT-5.4 发布的协同

GDPval 与 GPT-5.4 同步发布并非偶然。GPT-5.4 在 GDPval 上 83.0% 的突破性成绩是其"最强专业工作模型"定位的核心论据。这种"模型 + 基准同步发布"的策略也反映了 OpenAI 对评估体系话语权的重视。

### 与 GPT-5 加速科学研究的关联

此前"Early Experiments in Accelerating Science with GPT-5"探索了 AI 在科研领域的应用，而 GDPval 将评估范围从科研扩展到**44 个职业的广泛知识工作**，是"AI 加速专业工作"理念的系统化量化。

### 与 Operator / ChatGPT Agent 的关联

GDPval 测量的"知识工作"正是 Operator 和 ChatGPT Agent 等智能体系统要自动化的目标。GDPval 为这些系统的能力提供了**经济价值维度的量化基准**。

---

## 七、核心洞察

1. **评估范式转变**: 从"模型能答对多少题"到"模型能替代多少专业工作"，GDPval 直接连接 AI 能力与经济价值
2. **AI≠完美替代**: 29% 需修正、3% 灾难性错误的数据表明，"人类监督"（human-in-the-loop）仍不可或缺
3. **职业差异显著**: AI 在结构化文本工作（编辑 75%、销售管理 79%）远超在物理/创意工作（工程 17-23%、视频编辑 17%）的表现
4. **经济冲击量化**: 覆盖 $3 万亿薪酬的 44 个职业使 GDPval 成为预测 AI 经济影响的重要工具
5. **开源与透明**: 220 个黄金集任务的开源使外部研究者可独立验证和扩展

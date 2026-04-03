# Why SWE-bench Verified No Longer Measures Frontier Coding Capabilities

> 来源: https://openai.com/index/swe-bench-verified-analysis/
> 实际链接: https://openai.com/index/why-we-no-longer-evaluate-swe-bench-verified/
> 发布日期: 2026-02-23
> 类别: Research - 基准评估与方法论

---

## 一、核心概述

OpenAI 发布了对 **SWE-bench Verified** 基准的深度分析，指出该基准因**测试设计缺陷**和**数据污染（Data Contamination）** 已不再适合衡量前沿编码能力。OpenAI 宣布不再使用 SWE-bench Verified 进行评估，并推荐由 Scale AI 开发的 **SWE-bench Pro** 作为替代方案。这标志着 AI 编码评估领域的一个重要转折点。

---

## 二、SWE-bench Verified 的核心问题

### 2.1 测试设计缺陷 — "Too Narrow and Too Wide"

测试用例存在系统性设计问题：

**过窄（Too Narrow）示例**:
- 在任务 `django__django-14725` 中，测试要求使用名为 **`edit_only`** 的特定参数
- 但问题描述中**并未明确要求**该实现细节
- 测试实际上在验证**具体实现方式**而非**功能正确性**
- 合理的替代实现会被错误地判定为失败

**过宽（Too Wide）**:
- 部分测试对解决方案的验证不够充分
- 不完整或不正确的解决方案可能通过测试

### 2.2 数据污染问题

OpenAI 对多个前沿模型进行了系统性污染检测：

| 检测方法 | 说明 |
|---------|------|
| **Task ID probing** | 提供任务 ID，检查模型是否能回忆相关信息 |
| **Description probing** | 提供问题描述，检查模型是否能生成金标准补丁 |
| **Gold patch probing** | 检查模型是否能逐字复现参考解决方案 |
| **PR test probing** | 检查模型是否能复现 PR 测试代码 |

**关键发现**:
- **每个被测试的前沿模型**（GPT-5.2、Claude Opus 4.5、Gemini 3 Flash）都能对部分任务**逐字复现金标准补丁**
- 这构成了数据污染的**强有力证据**
- SWE-bench Verified 的仓库、代码库和发布说明全部开源且被广泛讨论，在模型训练中**几乎不可能避免污染**

### 2.3 基准饱和

前沿模型在 SWE-bench Verified 上的得分已趋于饱和：
- 多个模型得分超过 **80%**
- 基准已无法有效区分不同模型的编码能力
- 分数差异更多反映**污染程度**而非**真实能力**

---

## 三、SWE-bench Verified vs. SWE-bench Pro 对比

| 维度 | SWE-bench Verified | SWE-bench Pro |
|------|-------------------|---------------|
| **开发方** | Princeton NLP | Scale AI |
| **任务数量** | ~500 | **1,865** |
| **代码库** | 开源仓库 | 公开 + 保留 + **商业代码库** |
| **编程语言** | 主要 Python | **Python, Go, TypeScript, JavaScript** |
| **任务复杂度** | 中等 | **长时段任务**（专业工程师需数小时至数天） |
| **污染风险** | 高（全开源） | **低**（含保留和商业代码） |
| **评估有效性** | 已饱和 | 仍具区分度 |

---

## 四、前沿模型在两个基准上的表现差异

| 模型 | SWE-bench Verified | SWE-bench Pro | 差距 |
|------|-------------------|---------------|------|
| **Claude Opus 4.5** | 80.9% | 45.9% | -35.0% |
| **GPT-5** | ~80%+ | 23.3% (Pass@1) | -57%+ |

**巨大的分数差距**揭示了 Verified 分数的严重膨胀，Pro 更真实地反映了模型在企业级工程任务上的实际能力。

---

## 五、SWE-bench Pro 的设计特点

- **1,865 个长时段任务**，覆盖 **41 个活跃维护的仓库**
- 跨越 **4 种编程语言**（Python、Go、TypeScript、JavaScript）
- 包含**商业代码库**，难以在公开训练数据中找到
- 任务设计面向**企业级实际工程工作**
- 显式优化以**减少数据污染**

---

## 六、方法论贡献

### 6.1 污染检测方法论

OpenAI 提出的四维度污染检测方法（Task ID / Description / Gold Patch / PR Test probing）为基准评估领域提供了**系统性污染检测框架**，可应用于其他基准的可信度评估。

### 6.2 测试设计评估标准

"Too Narrow / Too Wide"分析框架为评估基准测试质量提供了**通用方法论**：
- 测试是否验证功能正确性而非实现细节？
- 测试是否能拒绝不完整的解决方案？

---

## 七、关联分析

### 与 GPT-5.4 / GPT-5.3-Codex 的关联

GPT-5.4 和 GPT-5.3-Codex 作为 OpenAI 最新的编码模型，其能力评估需要**可信的基准**。SWE-bench Verified 的失效直接影响了这些模型的评估策略。转向 SWE-bench Pro 意味着 OpenAI 对自身模型采用了**更严格的评估标准**（GPT-5 在 Pro 上仅 23.3%）。

### 与 Codex 生态的关联

**Introducing Codex** 和 **Codex Figma** 等产品的实际表现评估不应依赖已污染的基准。SWE-bench Pro 的长时段、多语言、企业级任务设计更接近 Codex 的实际使用场景。

### 与 GDPVal 基准的关联

**GDPVal Real World Benchmark** 同样关注评估方法论的可靠性。SWE-bench 分析与 GDPVal 研究共同反映了 OpenAI 对**基准可信度**的系统性关注。

---

## 八、核心洞察

1. **基准污染是行业性问题**: 所有被测试的前沿模型都存在污染证据，这不是某家公司的问题，而是当基准数据完全公开时的**必然结果**
2. **高分≠高能力**: SWE-bench Verified 上 80%+ 的分数与 SWE-bench Pro 上 23.3% 的分数形成鲜明对比，警示行业不应盲目追求基准分数
3. **评估方法需要持续进化**: 基准的有效生命周期有限，随着模型训练数据的扩张和能力提升，评估工具必须同步更新
4. **商业代码是抗污染利器**: SWE-bench Pro 引入商业代码库是对抗数据污染的有效策略，为基准设计提供了新范式
5. **OpenAI 的自我审视**: 主动公开自家模型在更难基准上的低分数（23.3%），体现了评估透明度和学术诚信

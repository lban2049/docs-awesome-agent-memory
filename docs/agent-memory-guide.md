# Agent Memory 完整指南

## 概述

Agent Memory（智能体记忆）是大语言模型（LLMs）和多模态大语言模型（MLLMs）领域的核心技术之一，它使 AI 系统能够实现长期上下文保持、信息检索和高效推理。本指南汇总了该领域的系统、基准测试、论文以及最新研究进展。

### 什么是 Agent Memory？

Agent Memory 是指 AI 智能体在交互过程中存储、组织和检索信息的能力。类似于人类记忆系统，Agent Memory 使 AI 能够：
- **保持长期上下文**：跨越多次对话记住用户偏好和历史信息
- **高效检索**：快速找到相关的历史信息来支持当前任务
- **持续学习**：从经验中学习并不断改进性能
- **个性化交互**：根据用户历史提供定制化的响应

### 为什么 Agent Memory 重要？

随着 AI 智能体在各个领域的应用日益广泛，记忆能力成为实现真正智能交互的关键：
- **突破上下文窗口限制**：传统 LLMs 受限于有限的上下文长度，记忆机制可以有效扩展这一限制
- **提升用户体验**：记住用户偏好和历史交互，提供更自然、连贯的对话体验
- **支持复杂任务**：在多步骤、长期任务中维持状态和进度
- **实现自主进化**：通过经验积累和反思，智能体可以不断改进自己的行为模式

### 本指南的使用方式

本指南面向以下读者：
- **研究人员**：寻找最新论文、基准测试和研究方向
- **开发者**：选择合适的开源记忆系统集成到项目中
- **学习者**：系统性了解 Agent Memory 的技术体系
- **技术决策者**：评估不同记忆方案的特点和适用场景

我们将资源分为以下几大类别：
1. **产品与系统**：可直接使用的开源和商业记忆系统
2. **教程与调研**：学习资源和综述性文献
3. **基准测试**：评估记忆系统性能的数据集和任务
4. **研究论文**：按记忆类型和应用场景分类的前沿研究
5. **学术活动**：相关的工作坊和会议

---

## 产品与开源系统

### 开源产品

以下开源项目按 GitHub star 数量排序，提供了不同的记忆系统实现方案。带 **粗体** 的项目表示有公开可复现的代码。

#### 1. Mem0

**项目地址**：https://github.com/mem0ai/mem0
**论文**：https://arxiv.org/abs/2504.19413
**官网**：https://mem0.ai/

Mem0 是目前最受欢迎的开源记忆系统之一，提供了简单易用的 API 来为 LLM 应用添加记忆功能。

**主要特点**：
- 简洁的 API 设计，易于集成
- 支持多种存储后端
- 提供用户级、会话级和全局级记忆管理

**替代方案 - TeleMem**：
- **项目地址**：https://github.com/TeleAI-UAGI/TeleMem
- 作为 Mem0 的直接替代品（`import vendor.TeleMem as mem0`）
- 新发布的上升项目，技术报告即将发布

#### 2. Zep (powered by Graphiti)

**项目地址**：https://github.com/getzep/graphiti
**论文**：https://arxiv.org/abs/2501.13956
**官网**：https://www.getzep.com/

基于图结构的记忆系统，利用知识图谱来组织和检索记忆。

**主要特点**：
- 使用图数据库存储记忆关系
- 支持复杂的语义检索
- 适合需要理解实体关系的应用场景

#### 3. Letta (原 MemGPT)

**项目地址**：https://github.com/letta-ai/letta
**论文**：https://arxiv.org/abs/2310.08560
**官网**：https://www.letta.com/

Letta（前身为 MemGPT）通过操作系统的虚拟内存管理思想来管理 LLM 的上下文。

**主要特点**：
- 分层记忆管理（工作记忆 + 长期记忆）
- 自主决定何时读写记忆
- 适合需要长期对话和复杂推理的场景

#### 4. Second Me

**项目地址**：https://github.com/mindverse/Second-Me
**论文**：https://arxiv.org/abs/2503.08102
**官网**：https://home.second.me/

个人化的 AI 助手记忆系统，专注于个人信息管理。

#### 5. Cognee

**项目地址**：https://github.com/topoteretes/cognee
**论文**：https://arxiv.org/abs/2505.24478
**官网**：https://www.cognee.ai/

优化知识图谱与 LLM 之间接口的记忆系统。

#### 6. Claude-Mem

**项目地址**：https://github.com/thedotmack/claude-mem
**官网**：https://claude-mem.ai/

专门为 Claude Code 设计的记忆插件。

**主要特点**：
- 与 Claude Code 深度集成
- 提供会话级记忆管理
- 简化 Claude 应用的记忆实现

#### 7. MIRIX

**项目地址**：https://github.com/Mirix-AI/MIRIX
**论文**：https://arxiv.org/abs/2507.07957
**官网**：https://mirix.io/

多智能体记忆系统，支持智能体之间的记忆共享和协作。

#### 8. MemOS

**项目地址**：https://github.com/MemTensor/MemOS
**论文**：https://arxiv.org/abs/2507.03724
**官网**：https://memos.openmemory.net/

记忆操作系统，提供统一的记忆管理接口。

#### 9-16. 其他开源项目

- **MemU** - https://github.com/NevaMind-AI/memU
- **OpenMemory** - https://github.com/caviraoss/openmemory
- **MemMachine** - https://github.com/MemMachine/MemMachine
- **Memobase** - https://github.com/memodb-io/memobase
- **EverMemOS** - https://github.com/EverMind-AI/EverMemOS/
- **LangMem** - https://github.com/langchain-ai/langmem（LangChain 生态系统的一部分）
- **Hindsight** - https://github.com/vectorize-io/hindsight
- **MemoryBear** - https://github.com/SuanmoSuanyangTechnology/MemoryBear

### 商业闭源产品

以下产品提供商业化的记忆服务，部分开放了研究论文或部分代码：

1. **Supermemory** - https://supermemory.ai/
2. **Memories.ai** - https://memories.ai/（提供研究论文）
3. **Mem 2.0** - https://get.mem.ai/
4. **Macaron Mind Lab** - https://macaron.im/mindlab
5. **TwinMind** - https://twinmind.com/

### 已归档项目

以下项目已不再维护，但仍有参考价值：

1. **Memvid** - https://github.com/Olow304/memvid
2. **Memary** - https://github.com/kingjulio8238/memary

---

## 教程与学习资源

### 2025 年教程

#### ACM SIGIR-AP 2025 Tutorial

**标题**：Conversational Agents: From RAG to LTM（对话智能体：从 RAG 到长期记忆）
**会议**：ACM SIGIR-AP 2025
**资源**：
- 论文：https://dl.acm.org/doi/10.1145/3767695.3769671
- 代码：https://github.com/TeleAI-UAGI/Awesome-Agent-Memory
- 网站：https://sites.google.com/view/ltm-tutorial

这是一个系统性介绍如何从 RAG（检索增强生成）过渡到长期记忆系统的教程，涵盖了最新的技术进展和实践方法。

#### Daily Dose of DS 实践系列

**标题**：A Practical Deep Dive Into Memory Optimization for Agentic Systems

这是一个三部分的深度实践教程：
- **Part A**：https://www.dailydoseofds.com/ai-agents-crash-course-part-15-with-implementation/
- **Part B**：https://www.dailydoseofds.com/ai-agents-crash-course-part-16-with-implementation/
- **Part C**：https://www.dailydoseofds.com/ai-agents-crash-course-part-17-with-implementation/

提供了记忆优化的实战代码和详细讲解。

---

## 调研与综述论文

综述论文帮助我们理解 Agent Memory 的研究全貌和发展趋势。

### 2025 年综述（带代码）

#### Memory in the Age of AI Agents

**论文**：https://arxiv.org/abs/2512.13564
**代码**：https://github.com/Shichun-Liu/Agent-Memory-Paper-List

**核心观点**：
- 系统性回顾了 AI 智能体时代的记忆机制
- 分析了不同记忆类型的优劣
- 提出了未来研究方向

#### Rethinking Memory in AI

**论文**：https://arxiv.org/abs/2505.00675
**代码**：https://github.com/Elvin-Yiming-Du/Survey_Memory_in_AI

**核心观点**：
- 提出了 AI 记忆的分类体系
- 讨论了记忆操作的基本原语
- 探讨了未来发展方向

#### A Survey on the Memory Mechanism of LLM-based Agents (2024)

**论文**：https://arxiv.org/abs/2404.13501
**代码**：https://github.com/nuster1128/LLM_Agent_Memory_Survey

这是 2024 年最具影响力的综述之一，系统性地总结了基于 LLM 的智能体记忆机制。

### 2025 年其他综述

- **From Human Memory to AI Memory**：https://arxiv.org/abs/2504.15965
  从人类记忆机制角度分析 AI 记忆

- **Cognitive Memory in Large Language Models**：https://arxiv.org/abs/2504.02441
  认知科学视角下的 LLM 记忆研究

- **Advances and Challenges in Foundation Agents (Chapter 3)**：https://arxiv.org/abs/2504.01990
  基础智能体的进展与挑战（第三章聚焦记忆）

- **Human-inspired Perspectives**：https://arxiv.org/abs/2411.00489
  人类启发的长期记忆研究

---

## 基准测试与评估

基准测试是评估记忆系统性能的重要工具。我们将其分为纯文本和多模态两大类。

### 纯文本基准测试

#### 2025 年基准测试（带代码/数据）

##### BEAM - Beyond a Million Tokens

**论文**：https://arxiv.org/abs/2510.27246
**代码**：https://github.com/mohammadtavakoli78/BEAM
**数据集**：https://huggingface.co/datasets/Mohammadta/BEAM

**特点**：
- 超过一百万 token 的长期记忆评估
- 测试记忆系统在极长上下文中的表现

##### MOOM - 超长角色扮演对话

**论文**：https://arxiv.org/abs/2509.11860（ZH-4O 论文）
**代码**：https://github.com/cows21/MOOM-Roleplay-Dialogue
**数据集**：https://github.com/cows21/MOOM-Roleplay-Dialogue/tree/main/data

**特点**：
- 专注于角色扮演场景的记忆维护
- 测试记忆的组织、优化和管理能力

##### PersonaMem - 动态用户画像

**论文**：https://arxiv.org/abs/2504.14225
**代码**：https://github.com/bowen-upenn/PersonaMem
**数据集**：
- PersonaMem：https://huggingface.co/datasets/bowen-upenn/PersonaMem
- ImplicitPersona：https://huggingface.co/datasets/bowen-upenn/ImplicitPersona

**特点**：
- 大规模动态用户画像构建
- 个性化响应生成评估

##### MemoryAgentBench - 增量多轮交互

**论文**：https://arxiv.org/abs/2507.05257
**代码**：https://github.com/HUST-AI-HYZ/MemoryAgentBench
**数据集**：https://huggingface.co/datasets/ai-hyz/MemoryAgentBench

**特点**：
- 通过增量多轮交互评估记忆能力
- 模拟真实对话场景

##### LifelongAgentBench - 终身学习

**论文**：https://arxiv.org/abs/2505.11942
**代码**：https://github.com/caixd-220529/LifelongAgentBench
**数据集**：https://huggingface.co/datasets/csyq/LifelongAgentBench

**特点**：
- 评估智能体的终身学习能力
- 长期记忆积累和应用

##### NoLiMa - 超越字面匹配

**论文**：https://arxiv.org/abs/2502.05167
**代码**：https://github.com/adobe-research/NoLiMa
**数据集**：https://github.com/adobe-research/NoLiMa/tree/main/data

**特点**：
- 超越字面匹配的长上下文评估
- 测试语义理解和推理能力

##### 其他 2025 年基准

- **MemoryBench** - 记忆与持续学习：https://arxiv.org/abs/2510.17281
- **HaluMem** - 记忆系统幻觉评估：https://arxiv.org/abs/2511.03506
- **LongBench v2** - 长上下文多任务理解：https://arxiv.org/abs/2412.15204
- **Minerva** - 可编程记忆测试：https://arxiv.org/abs/2502.03358
- **MemBench** - 全面记忆评估：https://arxiv.org/abs/2506.21605
- **Evo-Memory** - 自进化记忆：https://arxiv.org/abs/2511.20857
- **OdysseyBench** - 长期办公应用工作流：https://arxiv.org/abs/2508.09124

#### 2024 年经典基准

##### LongMemEval

**论文**：https://arxiv.org/abs/2410.10813
**数据集**：https://github.com/xiaowu0162/LongMemEval

评估聊天助手的长期交互记忆能力。

##### LoCoMo - 超长期对话记忆

**论文**：https://arxiv.org/abs/2402.17753
**代码**：https://github.com/snap-research/LoCoMo
**数据集**：https://github.com/snap-research/locomo/tree/main/data

Snap Research 发布的超长期对话记忆评估基准。

##### ∞Bench - 超过 10 万 Token

**论文**：https://arxiv.org/abs/2402.13718v3
**代码**：https://github.com/OpenBMB/InfiniteBench

评估超过 100K tokens 的长上下文理解能力。

##### LongBench - 双语多任务

**论文**：https://arxiv.org/abs/2308.14508
**代码**：https://github.com/THUDM/LongBench/blob/main/LongBench/README.md

双语（中英文）长上下文理解基准。

#### 2023 年基准

##### Storybench

**论文**：https://proceedings.neurips.cc/paper_files/paper/2023/hash/f63f5fbed1a4ef08c857c5f377b5d33a-Abstract-Datasets_and_Benchmarks.html
**代码**：https://github.com/google/storybench

持续故事可视化的多面基准测试。

### 多模态基准测试

#### 2025 年多模态基准（带代码）

##### TeleEgo - 野外自我中心 AI 助手

**论文**：https://arxiv.org/abs/2510.23981
**代码**：https://github.com/TeleAI-UAGI/TeleEgo
**项目页**：https://programmergg.github.io/jrliu.github.io/

**特点**：
- 第一人称视角的 AI 助手评估
- 真实场景下的记忆和理解能力测试

##### LVBench - 超长视频理解

**论文**：https://arxiv.org/abs/2406.08035
**代码**：https://github.com/zai-org/LVBench

评估极长视频的理解能力。

##### Video-MME - 视频分析综合评估

**论文**：https://arxiv.org/abs/2405.21075v3
**代码**：https://github.com/MME-Benchmarks/Video-MME

首个多模态 LLM 视频分析的综合评估基准。

#### 2024 年多模态基准

##### MovieChat+ - 稀疏记忆问答

**论文**：https://arxiv.org/abs/2404.17176
**代码**：https://github.com/rese1f/MovieChat

使用问题感知的稀疏记忆进行长视频问答。

##### CinePile - 长视频问答

**论文**：https://arxiv.org/abs/2405.08813
**数据集**：https://huggingface.co/datasets/tomg-group-umd/cinepile

电影场景的长视频问答数据集。

##### LongVideoBench - 交错视频语言理解

**论文**：https://arxiv.org/abs/2407.15754
**代码**：https://github.com/longvideobench/LongVideoBench

长上下文交错视频语言理解基准。

#### 2023 年多模态基准

##### EgoSchema - 超长视频语言理解

**论文**：https://proceedings.neurips.cc/paper_files/paper/2023/file/90ce332aff156b910b002ce4e6880dec-Paper-Datasets_and_Benchmarks.pdf
**代码**：https://github.com/egoschema/egoschema

NeurIPS 2023 发布的超长形式视频语言理解诊断基准。

##### LvBench

**论文**：https://arxiv.org/abs/2312.04817

长形式视频理解的多功能多模态问答基准。

---

## 研究论文

研究论文按记忆的实现方式和应用场景分类。

### 非参数记忆（Nonparametric Memory）

非参数记忆通过外部存储系统（如数据库、向量存储）来保存和检索信息，不修改模型参数。

#### 文本记忆

##### 2025 年研究（带代码）

###### LightMem - 轻量级记忆增强

**论文**：https://arxiv.org/abs/2510.18866
**代码**：https://github.com/zjunlp/LightMem

**核心思想**：
- 轻量级的记忆增强生成方法
- 降低记忆系统的计算和存储开销

###### Nemori - 认知启发的自组织记忆

**论文**：https://arxiv.org/abs/2508.03341
**代码**：https://github.com/nemori-ai/nemori

**核心思想**：
- 受认知科学启发的自组织记忆系统
- 模拟人类记忆的组织和检索机制

##### 2025 年其他文本记忆研究

- **O-Mem**：https://arxiv.org/abs/2511.13593 - 全方位记忆系统，支持个性化、长期和自进化
- **Omne-R1**：https://arxiv.org/abs/2508.17330 - 带记忆的推理系统，用于多跳问答
- **In Prospect and Retrospect**：https://aclanthology.org/2025.acl-long.413/ - 反思性记忆管理
- **SEDM**：https://arxiv.org/abs/2509.09498 - 可扩展的自进化分布式记忆
- **MemoRAG**：https://arxiv.org/abs/2409.05591 - 全局记忆增强的检索增强生成
- **Human-inspired Episodic Memory**：https://arxiv.org/abs/2407.09450 - 无限上下文的情景记忆
- **Towards LifeSpan Cognitive Systems**：https://arxiv.org/abs/2409.13265 - 面向终身认知系统

##### 2024 年经典研究（带代码）

###### COMEDY - 压缩记忆

**论文**：https://arxiv.org/abs/2402.11975
**代码**：https://github.com/nuochenpku/COMEDY

**核心思想**：
- 通过压缩技术在真实长期对话中释放压缩记忆的潜力
- 平衡记忆容量和检索效率

###### Agent Workflow Memory

**论文**：https://arxiv.org/abs/2409.07429
**代码**：https://github.com/zorazrw/agent-workflow-memory

**核心思想**：
- 工作流级别的记忆管理
- 跨任务的经验复用

###### MemoryBank

**论文**：https://ojs.aaai.org/index.php/AAAI/article/view/29946
**代码**：https://github.com/zhongwanjun/MemoryBank-SiliconFriend

**核心思想**：
- 使用记忆银行增强 LLM 的长期记忆能力
- 层次化的记忆组织

###### Temporal Memory

**论文**：https://arxiv.org/abs/2406.00057
**数据集**：https://github.com/Zyphra/TemporalMemoryDataset

**核心思想**：
- 具有上下文和时间敏感性的长期记忆
- 考虑时间因素的记忆更新和检索

##### 2024 年其他研究

- **InfLLM**：https://arxiv.org/abs/2402.04617 - 免训练的长上下文外推

##### 2023 年研究

- **RET-LLM**：https://arxiv.org/abs/2305.14322 - 通用读写记忆系统

#### 图记忆（Graph Memory）

图记忆使用图结构来组织和关联记忆信息，适合表示实体关系和知识网络。

##### 2025 年研究（带代码）

###### HippoRAG - 从 RAG 到记忆

**论文**：https://arxiv.org/abs/2502.14802
**代码**：https://github.com/OSU-NLP-Group/HippoRAG

**核心思想**：
- 从 RAG 过渡到非参数持续学习
- 受海马体启发的长期记忆机制

###### MIRIX - 多智能体记忆系统

**论文**：https://arxiv.org/abs/2507.07957
**代码**：https://github.com/Mirix-AI/MIRIX

**核心思想**：
- 基于图的多智能体记忆系统
- 支持智能体间的记忆共享和协作

###### Hierarchical Memory Organization

**论文**：https://aclanthology.org/2025.acl-long.1423/
**代码**：https://github.com/eugeneyujunhao/mog

**核心思想**：
- 层次化的记忆组织用于 Wikipedia 生成
- 结构化的知识表示

##### 2025 年其他图记忆研究

- **From Experience to Strategy**：https://arxiv.org/abs/2511.07800 - 可训练的图记忆
- **Bridging Intuitive Associations**：https://aclanthology.org/2025.findings-acl.901/ - 图结构长期记忆
- **HiAgent**：https://aclanthology.org/2025.acl-long.1575/ - 层次化工作记忆管理
- **Optimizing KG-LLM Interface**：https://arxiv.org/abs/2505.24478 - 优化知识图谱与 LLM 接口

##### 2024 年经典研究（带代码）

###### HippoRAG - 神经生物学启发

**论文**：https://arxiv.org/abs/2405.14831
**代码**：https://github.com/OSU-NLP-Group/HippoRAG

**核心思想**：
- 受神经生物学启发的长期记忆机制
- 模拟海马体的记忆编码和检索过程

###### AriGraph - 知识图谱世界模型

**论文**：https://arxiv.org/abs/2407.04363
**代码**：https://github.com/AIRI-Institute/AriGraph

**核心思想**：
- 使用知识图谱和情景记忆构建世界模型
- 支持复杂的推理和规划

#### 多模态记忆（用于理解）

多模态记忆处理图像、视频、音频等多种模态的信息，支持跨模态的记忆存储和检索。

##### 2025 年研究（带代码）

###### MemVerse - 终身学习的多模态记忆

**论文**：https://arxiv.org/abs/2512.03627
**代码**：https://github.com/KnowledgeXLab/MemVerse
**博客**：https://dw2283.github.io/memverse.ai/research

**核心思想**：
- 支持终身学习的多模态记忆系统
- 跨模态的记忆整合和检索

###### MGA - 记忆驱动的 GUI 智能体

**论文**：https://arxiv.org/abs/2510.24168
**代码**：https://github.com/MintyCo0kie/MGA4OSWorld

**核心思想**：
- 以观察为中心的 GUI 交互
- 视觉记忆驱动的界面操作

###### M3-Agent - 多模态长期记忆智能体

**论文**：https://arxiv.org/abs/2508.09736
**代码**：https://github.com/bytedance-seed/m3-agent

**核心思想**：
- 看、听、记、推的完整循环
- 多感官信息的统一记忆表示

###### HippoMM - 海马体启发的多模态记忆

**论文**：https://arxiv.org/abs/2504.10739
**代码**：https://github.com/linyueqian/HippoMM

**核心思想**：
- 受海马体启发的长期视听事件理解
- 神经科学与 AI 的结合

##### 2025 年其他多模态研究

- **Infinite Video Understanding**：https://arxiv.org/abs/2507.09068
- **Episodic Memory Representation**：https://arxiv.org/abs/2508.09486 - 长视频理解的情景记忆
- **Multi-RAG**：https://arxiv.org/abs/2505.23990 - 多模态检索增强生成
- **Contextual Experience Replay**：https://arxiv.org/abs/2506.06698 - 语言智能体的自我改进

##### 2024 年研究（带代码）

###### VideoAgent - 长视频理解智能体

**论文**：https://arxiv.org/abs/2403.10517
**代码**：https://github.com/HKUDS/VideoAgent

**核心思想**：
- 使用 LLM 作为智能体理解长视频
- 主动的信息检索和整合

###### VideoChat-Flash - 层次化压缩

**论文**：https://arxiv.org/abs/2501.00574
**代码**：https://github.com/OpenGVLab/VideoChat-Flash

**核心思想**：
- 长上下文视频建模的层次化压缩
- 高效的视频记忆表示

###### LongVLM - 高效长视频理解

**论文**：https://arxiv.org/abs/2404.03384
**代码**：https://github.com/ziplab/LongVLM

**核心思想**：
- 通过 LLM 实现高效的长视频理解
- 视觉记忆的压缩和检索

###### KARMA - 具身 AI 的记忆系统

**论文**：https://arxiv.org/abs/2409.14908
**代码**：https://github.com/WZX0Swarm0Robotics/KARMA/tree/master

**核心思想**：
- 长短期记忆系统增强具身 AI 智能体
- 机器人导航和操作的记忆支持

#### 多模态记忆（用于生成）

这类研究关注如何使用记忆来生成连贯、一致的多模态内容。

##### 2025 年研究（带代码）

###### MemFlow - 流动的自适应记忆

**论文**：https://arxiv.org/abs/2512.14699
**代码**：https://github.com/KlingTeam/MemFlow

**核心思想**：
- 长视频叙事的一致性和效率
- 自适应的记忆流动机制

###### MotionRAG - 运动检索增强

**论文**：https://arxiv.org/abs/2509.26391
**代码**：https://github.com/MCG-NJU/MotionRAG

**核心思想**：
- 运动检索增强的图像到视频生成
- 运动模式的记忆和复用

###### VideoRAG - 视频语料检索增强

**论文**：https://arxiv.org/abs/2501.05874
**代码**：https://github.com/starsuzi/VideoRAG

**核心思想**：
- 基于视频语料的检索增强生成
- 视频片段的记忆和重组

##### 2025 年其他生成研究

- **EgoLCD**：https://arxiv.org/abs/2512.04515 - 自我中心视频生成的长上下文扩散
- **Pack and Force Your Memory**：https://arxiv.org/abs/2510.01784 - 长形式一致性视频生成
- **Video World Models**：https://arxiv.org/abs/2506.05284 - 带长期空间记忆的视频世界模型
- **Mixture of Contexts**：https://arxiv.org/abs/2508.21058 - 长视频生成的上下文混合
- **Context as Memory**：https://arxiv.org/abs/2506.03141 - 场景一致的交互式长视频生成

### 参数化记忆（Parametric Memory）

参数化记忆通过修改模型参数本身来存储信息，或设计特殊的模型架构来增强记忆能力。

#### 2025 年研究（带代码）

##### MLP Memory

**论文**：https://arxiv.org/abs/2508.01832
**代码**：https://github.com/Rubin-Wei/MLPMemory

**核心思想**：
- 使用检索器预训练的外部记忆进行语言建模
- MLP 层作为记忆存储

##### Memory Decoder

**论文**：https://arxiv.org/abs/2508.09874
**代码**：https://github.com/LUMIA-Group/MemoryDecoder

**核心思想**：
- 预训练的即插即用记忆解码器
- 无需重新训练即可为 LLM 添加记忆

#### 2025 年其他参数化记忆研究

- **Nested Learning**：https://openreview.net/forum?id=nbMeRvNb7A - 深度学习架构的嵌套学习
- **Improving Factuality**：https://arxiv.org/abs/2412.18069 - 显式工作记忆提升事实性
- **R³Mem**：https://arxiv.org/abs/2502.15957 - 可逆压缩桥接记忆保留和检索
- **May the Memory Be With You**：https://dl.acm.org/doi/abs/10.1145/3721146.3721951 - 高效可更新状态
- **MeMo**：https://aclanthology.org/2025.findings-acl.785/ - 联想记忆机制
- **REFRAG**：https://arxiv.org/abs/2509.01092 - 重新思考基于 RAG 的解码
- **EpMAN**：https://aclanthology.org/2025.acl-long.574/ - 情景记忆注意力
- **Disentangling Memory and Reasoning**：https://aclanthology.org/2025.acl-long.84/ - 解耦记忆和推理

#### 2024 年经典研究（带代码）

##### InfLLM - 高效上下文记忆

**论文**：https://arxiv.org/abs/2402.04617
**代码**：https://github.com/thunlp/InfLLM

**核心思想**：
- 免训练的长上下文外推
- 高效的上下文记忆机制

##### MA-LMM - 记忆增强多模态模型

**论文**：https://openaccess.thecvf.com/content/CVPR2024/papers/He_MA-LMM_Memory-Augmented_Large_Multimodal_Model_for_Long-Term_Video_Understanding_CVPR_2024_paper.pdf
**代码**：https://github.com/boheumd/MA-LMM

**核心思想**：
- 记忆增强的大型多模态模型
- 长期视频理解

##### MemoryLLM - 自更新

**论文**：https://arxiv.org/abs/2402.04624
**代码**：https://github.com/wangyu-ustc/MemoryLLM

**核心思想**：
- 面向自更新的大语言模型
- 动态的参数化记忆更新

##### WISE - 终身模型编辑

**论文**：https://arxiv.org/abs/2405.14768
**代码**：https://github.com/zjunlp/EasyEdit

**核心思想**：
- 重新思考 LLM 终身模型编辑的知识记忆
- 知识更新和一致性维护

#### 2024 年其他研究

- **Titans**：https://arxiv.org/abs/2501.00663 - 测试时记忆学习
- **Memory³**：https://arxiv.org/abs/2407.01178v1 - 显式记忆的语言建模
- **Infinite-LLM**：https://arxiv.org/abs/2401.02669 - 分布式注意力和 KV 缓存
- **MemServe**：https://arxiv.org/abs/2406.17565 - 解耦式 LLM 服务的上下文缓存

#### 2023 年研究（带代码）

##### Augmenting Language Models

**论文**：https://arxiv.org/abs/2306.07174
**代码**：https://github.com/Victorwz/LongMem

**核心思想**：
- 使用长期记忆增强语言模型
- 缓存机制和记忆检索

##### PagedAttention

**论文**：https://arxiv.org/abs/2309.06180
**代码**：https://github.com/vllm-project/vllm

**核心思想**：
- 高效的内存管理机制（vLLM 项目）
- 分页注意力机制

### 智能体进化的记忆

这类研究关注记忆如何支持智能体的持续学习和自我改进。

#### 强化学习与持续学习

##### 2025 年研究（带代码）

###### ML-Master - AI-for-AI

**论文**：https://arxiv.org/abs/2506.16499
**代码**：https://github.com/sjtu-sai-agents/ML-Master

**核心思想**：
- 通过探索和推理的集成实现 AI-for-AI
- 自主的机器学习能力

###### MemEvolve - 元进化

**论文**：https://arxiv.org/abs/2512.18746
**代码**：https://github.com/bingreeky/MemEvolve

**核心思想**：
- 智能体记忆系统的元进化
- 自适应的记忆结构优化

###### Remember Me, Refine Me

**论文**：https://arxiv.org/abs/2512.10696
**代码**：https://github.com/agentscope-ai/ReMe

**核心思想**：
- 动态程序性记忆框架
- 经验驱动的智能体进化

###### MUSE - 从工作中学习

**论文**：https://arxiv.org/abs/2510.08002
**代码**：https://github.com/KnowledgeXLab/MUSE

**核心思想**：
- 经验驱动的自进化智能体
- 长期任务的在线学习

###### Mem-α - 强化学习构建记忆

**论文**：https://arxiv.org/abs/2509.25911
**代码**：https://github.com/wangyu-ustc/Mem-alpha

**核心思想**：
- 通过强化学习学习记忆构建方式
- 自适应的记忆策略

###### Memento - 无需微调 LLM

**论文**：https://arxiv.org/abs/2508.16153
**代码**：https://github.com/Agent-on-the-Fly/Memento

**核心思想**：
- 无需微调 LLM 即可微调智能体
- 基于记忆的行为调整

###### Goal-Directed Search

**论文**：https://arxiv.org/abs/2511.21726
**代码**：https://arxiv.org/abs/2511.21726

**核心思想**：
- 目标导向搜索优于目标无关的记忆压缩
- 任务相关的记忆检索

###### General Agentic Memory

**论文**：https://arxiv.org/abs/2511.18423
**代码**：https://github.com/VectorSpaceLab/general-agentic-memory/

**核心思想**：
- 通过深度研究实现通用智能体记忆
- 自主的知识发现和整合

###### AgentEvolver

**论文**：https://arxiv.org/abs/2511.10395
**代码**：https://github.com/modelscope/AgentEvolver

**核心思想**：
- 面向高效自进化的智能体系统
- 进化式的能力提升

###### FLEX - 前向经验学习

**论文**：https://arxiv.org/abs/2511.06449
**代码**：https://github.com/GenSI-THUAIR/FLEX

**核心思想**：
- 从经验中持续学习的智能体
- 前向学习避免灾难性遗忘

##### 2025 年其他进化研究

- **Beyond Heuristics**：https://arxiv.org/abs/2512.21567 - 决策理论框架的记忆管理
- **Nested Learning**：https://abehrouz.github.io/files/NL.pdf - 持续学习的新范式
- **LightSearcher**：https://arxiv.org/abs/2512.06653 - 基于经验记忆的高效深度搜索
- **Memory-R1**：https://arxiv.org/abs/2508.19828 - 通过强化学习管理记忆
- **Latent Learning**：https://arxiv.org/abs/2509.16189 - 情景记忆补充参数学习
- **Evo-Memory**：https://arxiv.org/abs/2511.20857 - 自进化记忆的基准测试
- **ReasoningBank**：https://arxiv.org/abs/2509.25140 - 推理记忆驱动的自进化
- **Long Term Memory**：https://arxiv.org/abs/2410.15665 - AI 自进化的基础
- **MemAgent**：https://arxiv.org/abs/2507.02259 - 基于 RL 的多对话记忆智能体
- **MemGen**：https://arxiv.org/abs/2509.24704 - 编织生成式潜在记忆
- **ReSum**：https://arxiv.org/abs/2509.13313 - 通过上下文摘要解锁长期搜索智能
- **MARC**：https://arxiv.org/abs/2510.07915 - 记忆增强的 RL Token 压缩
- **Continual Learning via Sparse Memory**：https://arxiv.org/abs/2510.15103 - 稀疏记忆微调
- **Task-Core Memory Management**：https://arxiv.org/abs/2505.09952 - 任务核心记忆管理

#### 上下文工程

##### 2025 年研究（带代码）

###### Everything is Context

**论文**：https://arxiv.org/abs/2512.05470
**代码**：https://github.com/AIGNE-io/aigne-framework

**核心思想**：
- 智能体文件系统抽象用于上下文工程
- 将所有信息视为可管理的上下文

##### 2025 年其他上下文工程研究

- **Agentic Context Engineering**：https://arxiv.org/abs/2510.04618 - 自我改进语言模型的上下文进化

---

## 认知科学中的记忆研究

这些研究从认知科学和神经科学的角度理解记忆，为 AI 记忆系统提供理论基础。

### 2025 年研究

#### Neural Population Activity for Memory

**论文**：https://www.cell.com/neuron/fulltext/S0896-6273(25)00854-2

**核心观点**：
- 记忆的神经群体活动特性
- 计算和编码方式

#### How Prediction Error Drives Memory Updating

**论文**：https://www.cell.com/trends/neurosciences/abstract/S0166-2236(25)00189-4

**核心观点**：
- 预测误差如何驱动记忆更新
- 蓝斑核-海马体交互的作用

#### Towards LLMs with Human-Like Episodic Memory

**论文**：https://www.cell.com/trends/cognitive-sciences/abstract/S1364-6613(25)00179-2

**核心观点**：
- 面向具有类人情景记忆的大语言模型
- 认知科学视角下的 AI 记忆设计

---

## 文章与博客

### 2025 年文章

#### Survey of AI Agent Memory Frameworks

**链接**：https://www.graphlit.com/blog/survey-of-ai-agent-memory-frameworks

全面调研各种 AI 智能体记忆框架的特点和应用。

### 2024 年文章

#### Memory in Language Model-Enabled Agents

**链接**：https://yuweisunn.github.io/blog-1-06-24.html

深入探讨语言模型驱动的智能体中的记忆机制。

#### Mastering LLM Memory

**链接**：https://www.strongly.ai/blog/mastering-llm-memory-a-comprehensive-guide.html

掌握 LLM 记忆的全面指南。

### 2023 年经典文章

#### LLM Powered Autonomous Agents

**作者**：Lilian Weng
**链接**：https://lilianweng.github.io/posts/2023-06-23-agent/

Lilian Weng 的经典博客文章，详细介绍了 LLM 驱动的自主智能体，包括记忆系统的设计。

---

## 学术工作坊与会议

### 2025 年工作坊

#### ACL 2025 - L2M2 Workshop

**会议**：ACL 2025
**名称**：The First Workshop on Large Language Model Memorization (L2M2)
**网站**：https://sites.google.com/view/memorization-workshop
**论文集**：https://aclanthology.org/volumes/2025.l2m2-1/

首届大语言模型记忆化工作坊，聚焦 LLM 的记忆机制、隐私问题和优化方法。

---

## 技术分类体系总结

### 按记忆类型分类

1. **非参数记忆（Nonparametric Memory）**
   - 文本记忆：使用文本数据库、向量数据库等
   - 图记忆：使用知识图谱组织记忆
   - 多模态记忆：处理图像、视频、音频等多模态信息

2. **参数化记忆（Parametric Memory）**
   - 通过模型参数编码记忆
   - 特殊架构设计（如记忆解码器、记忆层）

### 按应用场景分类

1. **对话系统**：长期对话记忆、用户画像
2. **内容生成**：视频生成、故事续写的一致性
3. **知识问答**：多跳推理、长文档理解
4. **具身智能**：机器人导航、任务规划
5. **智能体进化**：强化学习、持续学习

### 按记忆操作分类

1. **记忆编码**：如何将信息存入记忆
2. **记忆检索**：如何找到相关记忆
3. **记忆更新**：如何更新过时信息
4. **记忆遗忘**：如何选择性遗忘
5. **记忆整合**：如何组织和关联记忆

---

## 如何选择合适的记忆系统？

### 根据应用场景选择

#### 对话应用
- **推荐**：Mem0、Letta、MemoryBank
- **特点**：需要用户级记忆、会话记忆、长期偏好管理

#### 知识密集型应用
- **推荐**：HippoRAG、Graphiti、Cognee
- **特点**：需要复杂的语义检索、实体关系理解

#### 视频/多模态应用
- **推荐**：MA-LMM、VideoAgent、M3-Agent
- **特点**：需要处理视觉、音频等多模态信息

#### 具身智能/机器人
- **推荐**：KARMA、MemVerse
- **特点**：需要空间记忆、任务记忆、传感器数据集成

### 根据技术栈选择

#### Python + LangChain
- **推荐**：LangMem
- **优势**：与 LangChain 生态系统无缝集成

#### Claude 应用
- **推荐**：Claude-Mem
- **优势**：专为 Claude 优化

#### 需要自定义
- **推荐**：从论文实现或基于 Mem0/Letta 二次开发
- **优势**：完全控制记忆机制

---

## 研究趋势与未来方向

### 当前热点

1. **超长上下文处理**
   - 百万 token 级别的记忆管理
   - 高效的压缩和检索技术

2. **多模态记忆整合**
   - 视觉、听觉、文本的统一表示
   - 跨模态的记忆检索

3. **自进化智能体**
   - 从经验中学习的记忆机制
   - 强化学习驱动的记忆优化

4. **认知科学启发**
   - 模拟人类海马体的记忆机制
   - 情景记忆、语义记忆、程序性记忆的区分

### 未来方向

1. **更高效的记忆表示**
   - 减少存储和计算开销
   - 动态的记忆压缩和扩展

2. **隐私保护的记忆**
   - 联邦学习式的记忆管理
   - 差分隐私的记忆机制

3. **可解释的记忆**
   - 理解记忆的形成和检索过程
   - 可视化记忆结构

4. **跨智能体的记忆共享**
   - 多智能体协作的记忆机制
   - 知识迁移和经验复用

---

## 贡献与更新

本资源列表由 TeleAI 的 Ubiquitous AGI 团队维护。

### 如何贡献

如果您发现了新的相关资源或发现了错误，欢迎通过以下方式贡献：
1. 在 GitHub 上提交 Issue
2. 提交 Pull Request
3. 联系维护团队

### 资源标准

我们优先收录以下资源：
- ✅ 开源且代码可复现的项目（标记为粗体）
- ✅ 发表在顶级会议/期刊的论文
- ✅ 有实际应用价值的产品和工具
- ✅ 高质量的教程和综述

### 更新频率

- 每月更新最新的论文和项目
- 持续跟踪主要会议（ACL、NeurIPS、ICLR 等）
- 及时添加新发布的开源系统

---

## Star History

如果您觉得这个项目有帮助，请在 GitHub 上给我们一个 ⭐️！

[![Star History Chart](https://api.star-history.com/svg?repos=TeleAI-UAGI/Awesome-Agent-Memory&type=date&legend=top-left)](https://www.star-history.com/#TeleAI-UAGI/Awesome-Agent-Memory&type=date&legend=top-left)

---

## 许可证

本项目采用开源许可证，详见 LICENSE 文件。

---

**制作团队**：TeleAI Ubiquitous AGI Team

<div align="center">
  <img src="https://github.com/TeleAI-UAGI/TeleEgo/blob/main/assets/TeleAI.jpg" alt="TeleAI Logo" width="120px" />
</div>

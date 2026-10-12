# 术语表（参考卡）— CS329Z Lecture 1–5 教学空间

> 用法：自测时先遮住右列。与课件/一手资料口径一致。
> 版本：v3 + Lecture02–05 增补（2026-10-09）。各讲术语见文末各节（每节标注源文件夹）。

## 核心范式

| 术语 | 含义 | 出自 |
| --- | --- | --- |
| AI 模型 | 一个统计模型（如预测下一 token 的 Transformer） | BAIR 博客 |
| 复合 AI 系统 | 多个相互作用组件解决任务的系统：多次调模型+检索器+外部工具 | BAIR 博客 |
| workflow | 代码固定步骤的复合系统（例 Agentless、AlphaCode2） | 课件 p56 |
| agent / agentic | 由 LLM 决定步骤的复合系统（例 SWE-agent、ReAct） | 课件 p56 |
| agent loop | Obs→Think→Act→Obs 的执行循环 | ReAct (Yao 2022) |

## 智能体解剖（课件 p29-30）

| 术语 | 含义 |
| --- | --- |
| LLM Core | 大脑本体：思考与生成语言 |
| Planning & Reasoning | "下一步干什么才离目标更近" |
| Memory | 轨迹与经验的存储（traces so far） |
| Tools | 手：检索/计算器/代码/搜索/读写文件 |
| Environment | 外部世界：桌面OS/浏览器/数据库/设备 |
| 三层抽象 | 系统层（架构）/ 数据层（示例上下文）/ 评估层（指标） |

## 推理方法

| 术语 | 含义 |
| --- | --- |
| CoT 思维链 | 先一步步推理再答；弱点=幻觉 |
| ReAct | 推理+行动交错，观察回喂缓解幻觉 |
| Self-Consistency | 多条 CoT 路径，取最一致答案（投票） |
| Reflexion | 自然语言反思失败轨迹，存为"自提示" |
| 多智能体辩论 | 多个 LLM 各自推理再互相辩（Du 2023） |
| Orchestrator | 单一编排器协调多子 agent（Magentic-One） |

## 记忆（课件 p46-49，区分点=写入方式）

| 术语 | 含义 |
| --- | --- |
| episodic 情景记忆 | 存经历：追加式事件流写入 / 启发式打分检索 |
| semantic 语义记忆 | 存知识：LLM 对事件推理后写入 / 检索读取 |
| procedural 程序记忆 | 存技能：代码技能写入 / 向量嵌入检索（Voyager） |

## 复合系统组件

| 术语 | 含义 |
| --- | --- |
| RAG | 检索→增强（拼上下文）→生成；实时连接外部知识 |
| 工具调用四步 | Select 选 → Arguments 填参 → Validate 校验 → Execute 沙箱执行 |
| constrained decoding | 受限解码：生成时强制参数合法 |
| Toolformer | 训练 LM 自学调 API（选哪个/何时/传什么参/怎么用结果） |
| Gorilla | LLM 对接海量 API（Patil 2023） |
| MCP | Model Context Protocol：模型↔工具统一接口，M×N 集成变 M+N |

## 可靠性 / 评估 / 安全

| 术语 | 含义 |
| --- | --- |
| consistency 一致性 | 同一任务给两次，结果是否相同 |
| robustness 鲁棒性 | 对 prompt/工具的微小真实扰动是否稳定 |
| predictable failure | 失败是否可读、可恢复、可预期 |
| capability-reliability gap | 能力（成功率）高但可靠性跟不上（HAL Dashboard） |
| 弹窗攻击 | 恶意弹窗带偏计算机 agent，成功率 87% |
| sycophancy 谄媚 | 模型迎合用户而非正确 |
| PrivacyLens | 评估 LLM 行动中的隐私规范意识 |

## 必记数值（大白话+工程影响）

| 数值 | 含义 |
| --- | --- |
| 48.1 → 67.0 → 95.1 | GPT-3.5 零样本 → GPT-4 零样本 → GPT-3.5+agent循环（HumanEval）。换模型+19pp，套循环+47pp：改系统>换模型 |
| 60% / 30% | Databricks：60% LLM 应用用 RAG、30% 用多步链——组合是行业默认 |
| 0.95^10 ≈ 60% | 单步 95% 串 10 步只剩 6 成：串联系统看最弱环节，错误会复合 |
| 87% | 弹窗攻击把 agent 从原任务带偏的成功率：外部内容必须白名单过滤 |
| ~30% → ~80% | 最强 LLM 编程竞赛 30%，系统思路（采样+筛选）提到 80% |

## Week2 术语（CS329Z Lecture 2 + Anthropic 工程文章）

| 术语 | 含义 |
| --- | --- |
| attention / Q·K·V | Query 想找什么 / Key 能提供什么 / Value 实际内容；Softmax((Q·Kᵀ)/√dk)·V |
| O(n²) 上下文 | 每个 token 对每个 token 算注意力 → n² 对关系；长上下文昂贵的根因（p61） |
| causal mask | 因果掩码：训练时不许看未来的 token（p37） |
| multi-head | 多组 WQ/WK/WV 并行，各头学不同关注模式（p44-48） |
| residual / Layer Norm | 残差把输入加回 + 层归一化，让深层网络可训练 |
| linear attention | 去掉 Softmax + 改结合律，先算 Kᵀ·V 得固定状态 S；O(n) 复杂度、常量内存，但长文召回变弱（p87） |
| 混合注意力 | 少数全局注意力层 + 多数线性注意力层（Kimi K3, p90） |
| 交叉熵损失 | Loss = -log P(正确词)；训练=压低它（p100） |
| 预训练 / 中训练 / 后训练 | 学常识 / 领域数据配比倾斜 / 指令+偏好对齐（p101-118） |
| RLHF | 人类偏好排序→奖励模型→RL；坑=谄媚、装权威（p114-115） |
| RLVR | 用可自动验证的奖励做 RL（单元测试/Lean/精确匹配）；注意验证器设计（p116） |
| Prefill / Decode | 提示一次性算（算力受限，定 TTFT）/ 逐字吐（带宽受限，定 TPS）（p120-135） |
| KV Cache | 缓存已算的 K、V，Decode 不重算；省算力、吃显存、与前缀绑定（p133） |
| 投机解码 | 小草稿模型猜几个 token、大模型并行校验；可预测领域收益大（p136） |
| 推理期扩展 | 不动参数、多花算力换准确率（CoT / 重复采样 / 自洽 / 推理档位）（p138-148） |
| 约束解码 | 用 FSM 在生成时剪掉非法 token，强制合法结构（SGLang, p153） |
| DSPy 签名 | 声明输入输出字段（question->answer），自动生成提示+解析（p155） |
| context rot | 上下文越长，准确召回越差；attention n² 摊薄的后果（p163） |
| 上下文工程 | 策展推理时的最优 token 集合（含系统提示/工具/历史/记忆），迭代进行 |
| compaction 压缩 | 总结快满的对话、用摘要重开窗口；最轻形式=清工具结果（p171） |
| 结构化笔记 | agent 把进度写到窗口外文件（NOTES.md/to-do），之后读回 |
| 子智能体 | 子任务在干净窗口深挖，只回传 1-2k token 摘要 |
| 即时检索 just-in-time | 只留轻量标识（路径/查询），运行时按需加载（Claude Code 混合策略） |
| workflow 五模式 | 提示链 / 路由 / 并行化（sectioning·voting）/ 编排者-工作者 / 评估者-优化者 |
| ACI | Agent-Computer Interface：像做 HCI 一样做工具设计（防呆/示例/参数自解释） |

## Week3 术语（CS329Z Lecture 3: RAG + Agents）

| 术语 | 含义 |
| --- | --- |
| retriever-reader | 两段式开放域 QA：检索器粗筛 K 篇 → 阅读器在 K 篇里找答案（K 常 100） |
| RAG 两部件 | retriever p(z\|x) + generator p(y\|x,z)；p(y\|x)≈Σ p(z\|x)p(y\|x,z) |
| RAG-Sequence / RAG-Token | 整段答案用同一篇段落 / 每生成一个 token 可重选段落 |
| 分块 chunking | 把文档切成检索单位；固定大小 100-500 token、重叠 10-20% / 语义 / 上下文增强 / AI 动态 |
| ANN 近似最近邻 | IVF（只探最近簇）/ PQ（压缩向量）/ HNSW（多层跳图 ~log N） |
| HNSW | 分层可导航小世界：底层全量、上层稀疏，从顶层贪心下降 |
| Contextual Retrieval | LLM 给每块生成背景拼进 chunk 再嵌入（Anthropic） |
| Late Chunking | 先整篇编码再按块 mean-pool，背景压在向量里、无 LLM 调用 |
| RAPTOR | 自底向上建摘要树，跨层检索（细节命中叶子、主题命中上层） |
| BM25 | 词重叠打分：IDF × 词频饱和(k1) × 长度归一(b)；抓精确字面 |
| DPR | 稠密双编码器：p(z\|x)∝exp(d(z)ᵀq(x))；对比学习+批内/BM25硬负例；1000 对超 BM25 |
| ColBERT / 晚期交互 | 每 token 一向量，各自编码、打分时才交互；MaxSim；索引大 |
| MaxSim | S(q,d)=Σ_i max_j (q_i·d_j)：每个 query 词取段落里最像的再累加 |
| Cross-encoder | query+段拼一起过模型全注意力；准但无法扫全库（仅重排） |
| Hybrid Search + RRF | 两个检索器都跑再融合；RRF(d)=Σ1/(k+rank)，k=60，只融位置不融分数 |
| Hit@k / Failed@k | 前 k 有没有相关 / 一个都没有（=1−Hit@k） |
| Recall@k | 所有相关里找回了多少 |
| MRR@k | 第一个相关段排名倒数的平均 |
| nDCG@k | 相关性按位置折扣(log2(i+1))后归一，综合衡量找到+排序 |
| Agentic RAG | 把检索变成 agent 动作；三决策：查不查 / 查什么 / 够不够 |
| Self-RAG | 模型自学检索+自我批判（反思标记） |
| CRAG | critic 给检索结果打相关性分/置信度，触发不同检索动作 |
| Search-R1 | 用 RL 优化多轮搜索的推理轨迹（学搜索策略） |
| RAG 失败三侧 | 检索侧（召回天花板/索引过期/权限泄漏）/ 阅读侧（lost in middle/干扰/证据冲突）/ 循环侧（错误复合/无停止规则/提示注入） |
| Lost in the middle | 长上下文中间位置的信息被忽略（位置偏置） |

## Week4 术语（CS329Z Lecture 4: Tool Use）

| 术语 | 含义 |
| --- | --- |
| 工具 tool | 运行在 LM 外部的程序的函数接口，由 LM 生成调用与参数（Wang et al. 2024） |
| LLM 三类做不到 | 算不了（算术/多步逻辑/精确运算）、没见过（长尾/截止后/私有）、够不着（API/物理世界/实时状态） |
| Toolformer | LM 自学"调哪个/何时/传什么/怎么用结果"；自监督 + 损失过滤（Schick 2023） |
| 损失过滤 | 只保留"能降低后续 token 预测损失"的 API 调用 |
| ToolkenGPT | 每个工具学成一个 token（toolken）embedding，触发即切工具模式（Hao 2024） |
| ToolLLM/ToolBench | 16k+ 真实 API + 神经 API 检索器，ToolLLaMA（Qin 2023） |
| Gorilla | 1.6k API 微调；RAT 检索感知训练；AST 子树匹配测幻觉（Patil 2023） |
| RAT 检索感知训练 | 训练时混入正确/错误检索结果，让模型对低质检索鲁棒 |
| REST API | 面向人：端点+文档，无机器可读契约，模型须手写请求 |
| Function Calling | 面向模型：每工具一个 JSON schema，模型输出 name+args，harness 校验分发 |
| MCP | 面向生态：一个协议任何客户端；Server 暴露 tools/resources/prompts，运行时发现 |
| MCP 三角色 | Host（LLM 应用，管生命周期/权限/同意）/ Client（1:1 连 Server）/ Server（提供能力） |
| JSON-RPC 2.0 | MCP 的消息格式；有状态连接 + 能力协商 |
| 能力协商 | initialize 时双方声明支持的特性，决定会话可用的功能 |
| tools/list | 发现工具：返回 name/description/inputSchema 列表 |
| tools/call | 执行工具：name+arguments → content 数组 |
| 入站/出站鉴权 | inbound（agent→MCP server）与 outbound（server→后端 API）两套令牌 |
| BFCL | Berkeley Function-Calling Leaderboard：AST 离线 + 真实执行评估函数调用 |
| τ-bench | Tool-Agent-User 多轮交互基准（Yao 2024） |
| Pass^k | 连续 k 次都成功的概率——衡量可靠性/一致性（对比 Pass@k 至少一次成功） |
| 工具失败三层 | 单次（选错/参数错/幻觉工具）/ 多步链（顺序/恢复）/ 对话（策略/交互/不确定性） |

## Lecture05 术语（Frameworks & Orchestration，源文件夹 week3-10.7）

| 术语 | 含义 |
| --- | --- |
| 三支柱 | Data（数据/rollouts/示范/反馈）/ System or Model（LM/复合系统/agent）/ Eval（指标评测） |
| 框架谱系 | Model（逻辑在程序外）→ Workflow/复合系统（逻辑在程序里）→ Agent（控制流归 AI 模型） |
| DSPy | 把 LM pipeline 抽象为文本变换图；签名+模块+优化器；编译器按指标优化 |
| Signatures 签名 | 严格定义模型的输入/输出契约（What） |
| Modules 模块 | 组合签名与程序逻辑成可调用函数（How）；dspy.Predict/ChainOfThought/BestOfN |
| Optimizers 优化器 | 在给定 Data+Metric 下改进提示/权重（编译器） |
| dspy.ReAct / dspy.RLM | DSPy 内置让 agent 履行签名的模块 |
| LangGraph | 图编排：State（共享工作区）+ Node（读写 state 的函数）+ Edge（控制流） |
| 条件边 Conditional Edge | 实现分支工作流的边 |
| create_agent | LangGraph 内置创建 agent 的工具 |
| Agent Harness | 包裹模型的外壳：工具/记忆/上下文管理/执行的设计 |
| Mini SWE-Agent | 只有 bash、线性历史、subprocess 无状态执行 |
| OpenHands | 事件溯源（每步一 JSON）、持久终端（tmux） |
| Pi Agent | 4 个工具（read/write/edit/bash）、树状历史、无权限系统、刻意简单 |
| OpenClaw | 每 30 分钟自唤醒、常驻 Gateway、Markdown 身份文件、夜间整理记忆 |
| Temporal | 编排/持久执行：Activity（可失败单元）+ Workflow（连接）+ Execution History & State |
| Durable Workflow | 持久执行：崩溃后可恢复、可重试 |
| 可观测性工具 | MLflow / LangSmith / LangFuse（追踪与监控） |
| 四条工程铁律 | 保持简单 / 让失败可观察可恢复 / 跑评估 / 懂底层 |
| 工程循环 | Build → Run → Evaluate → Improve |





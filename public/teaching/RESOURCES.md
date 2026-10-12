# AI Agents / 复合 AI 系统 Resources

## Knowledge（高质量一手资料）

- [论文/博客: The Shift from Models to Compound AI Systems — Matei Zaharia 等 (BAIR, 2024-02)](https://bair.berkeley.edu/blog/2024/02/18/compound-ai-systems/)
  复合 AI 系统的奠基性论述：为什么结果来自"系统"而非"模型"，四大理由、系统设计空间、三大挑战(DSPy/FrugalGPT/LLMOps)。用在哪都用——week1 主线。
- [课件: Stanford CS 329Z Lecture 1 "Intro to Agentic Systems" — Diyi Yang, Michael Ryan, John Yang](http://web.stanford.edu/class/cs329z)
  智能体入门权威课件(本地副本: week1/slides/lecture01.pdf)：历史、智能体解剖(LLM Core/规划/记忆/工具/环境)、ReAct/CoT/Reflexion、记忆三类、RAG/工具/MCP、关键挑战与安全。
- [文章: Four AI Agent Strategies That Improve GPT-4 and GPT-3.5 Performance — Andrew Ng (The Batch, 2024-03)](https://www.deeplearning.ai/the-batch/how-agents-can-improve-llm-performance)
  四大智能体设计模式(反思/工具/规划/多智能体协作) + HumanEval 硬数据(GPT-3.5 48.1%→GPT-4 67%→GPT-3.5+agent loop 95.1%)。
- [论文: Towards Execution-Grounded Automated AI Research — Si et al. (Stanford, arXiv:2601.14525, 2026-01)](本地副本: week1/slides/Towards Execution-Grounded Automated AI Research.pdf)
  把"智能体想法→自动实现→GPU执行→进化搜索/RL反馈"跑通的前沿研究；自动执行器(Implementer/Scheduler/Worker)、对比表、RL 多样性崩塌。
- [论文: ReAct — Yao et al., 2022](https://arxiv.org/abs/2210.03629)
  智能体环路(Obs→Think→Act)的原始论文，week1 的核心架构来源。
- [博客: Lilian Weng "LLM Powered Autonomous Agents" (2023-06)](https://lilianweng.github.io/posts/2023-06-23-agent/)
  智能体组件(规划/记忆/工具)的经典总结，与课件 2.2 直接呼应。
- [论文: Reflexion — Shinn et al., 2023](https://arxiv.org/abs/2303.11366) 反思模式原始论文。
- [论文: Self-Consistency — Wang et al., 2023](https://arxiv.org/abs/2203.11171) 多次推理取一致答案。
- [文档: Model Context Protocol (MCP)](https://modelcontextprotocol.io/) 模型-工具统一协议，课件 Part 3 提到的基础设施方向。

## Knowledge — Week2（CS329Z Lecture 2 + Anthropic 工程文章）

- [课件: Stanford CS 329Z Lecture 2 "LLMs for Builders" — Diyi Yang, Michael Ryan, John Yang](http://web.stanford.edu/class/cs329z)
  本地副本: week2/lecture02.pdf（176 页）。涵盖：语言模型采样/解码、Transformer 架构（attention、multi-head、causal mask、residual/LN）、线性注意力（O(n²)→O(n)、DeltaNet、混合架构）、训练三阶段（预训练数据管线/中训练/后训练 RLHF·RLVR·SWE-Smith agent 训练）、推理（Prefill/Decode、Roofline、KV Cache、投机解码）、推理期扩展（CoT/重复采样/自洽）、结构化 I/O（约束解码 SGLang/DSPy 签名/分类头）、上下文工程（context rot、bloat、compaction、RLM）。week2 主线。
- [文章: Building effective agents — Anthropic (2024-12-19)](https://www.anthropic.com/engineering/building-effective-agents)
  workflow 与 agent 的架构区分、五种 workflow 模式（提示链/路由/并行化/编排者-工作者/评估者-优化者）、agents、三条核心原则（简单/透明/ACI）、Appendix 2（工具提示工程、poka-yoke、SWE-bench 绝对路径案例）。week2 第 22 课主线。
- [文章: Effective context engineering for AI agents — Anthropic (2025-09-29)](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
  上下文工程 vs 提示工程、context rot（Chroma 研究）、上下文解剖（system prompt 的"正确高度"/工具/examples）、即时检索 vs 预先检索、长程三招（compaction/结构化笔记/子智能体）。week2 第 20-21 课主线。
- [论文: Attention Is All You Need — Vaswani et al., 2017](https://arxiv.org/abs/1706.03762) Transformer 原始论文（lecture02 p27 引用）。
- [论文: RULER — What's the Real Context Size of Your Long-Context LMs](https://arxiv.org/abs/2404.06654) 长上下文基准（lecture02 p84，线性注意力长文更弱的证据）。
- [论文: SWE-smith: Scaling Data for Software Engineering Agents — arXiv:2504.21798](https://arxiv.org/abs/2504.21798) agent 专用训练（lecture02 p117-118）。
- [论文: Chain-of-Thought / Self-Consistency / Large Language Monkeys] CoT(arXiv:2201.11903) / 自洽(arXiv:2203.11171) / 重复采样(arXiv:2407.21787)，lecture02 p139-148。

## Knowledge — Week3（CS329Z Lecture 3: RAG + Agents）

- [课件: Stanford CS 329Z Lecture 3 "RAG + Agents" — Diyi Yang](http://web.stanford.edu/class/cs329z)
  本地副本: week3/lecture03.pdf（63 页）。涵盖：Why RAG、retriever-reader 框架、RAG 管线（RAG-Sequence/Token）、索引（四种分块、向量检索 IVF/PQ/HNSW）、上下文检索（Contextual Retrieval / Late Chunking / RAPTOR / GraphRAG）、检索器（BM25 公式 / DPR）、ColBERT 晚期交互、混合检索与 RRF、检索指标（Hit@k/Failed@k/Recall@k/MRR@k/nDCG@k）、Agentic RAG（Self-RAG/CRAG/Search-R1）、RAG 失败模式（检索侧/阅读侧/循环侧）。week3 主线。
- [论文: Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks — Lewis et al. (2021)](https://arxiv.org/abs/2005.11401)
  RAG 原始论文（本地: week3/…pdf）：参数化记忆(seq2seq)+非参数化记忆(Wikipedia 稠密索引)，RAG-Sequence/RAG-Token 两式，在 3 个开放域 QA 上 SOTA。week3 第 23 课主线。
- [论文: ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction over BERT — Khattab & Zaharia (SIGIR 2020)](https://arxiv.org/abs/2004.12832)
  晚期交互（late interaction）+ MaxSim；效果媲美 BERT 交叉编码器，快两个数量级、FLOPs 少四个数量级（本地: week3/…pdf）。week3 第 27 课主线。
- [论文: DPR — Dense Passage Retrieval for Open-Domain Question Answering — Karpukhin et al. (2020)](https://arxiv.org/abs/2004.04906) 稠密双编码器检索，对比学习 + 硬负例；1000 对 QA 即可超 BM25（lecture03 p43-48）。
- [文档: Contextual Retrieval — Anthropic](https://www.anthropic.com/engineering/contextual-retrieval) 用 LLM 给每块补背景 + 混合检索（lecture03 p27-29）。
- [论文/方法: Late Chunking (Günther et al., 2024) / RAPTOR (Sarthi et al., 2025) / GraphRAG (Edge et al., 2024)] 三种进阶索引（lecture03 p30-35）。
- [论文: Self-RAG (Asai et al., 2024) / CRAG (Yan et al., 2024) / Search-R1 (Jin et al., 2025)] Agentic RAG 三路线（lecture03 p56-61）。

## Knowledge — Week4（CS329Z Lecture 4: Tool Use）

- [课件: Stanford CS 329Z Lecture 4 "Tool Use" — Diyi Yang](http://web.stanford.edu/class/cs329z)
  本地副本: week3-10.5/lecture04.pdf（68 页）。涵盖：RAG 收尾（lost-in-the-middle、引用幻觉）、Why tools（三类做不到）、工具定义、Toolformer、Gorilla/ToolLLM/ToolkenGPT、标准接口三代（REST/函数调用/MCP）、MCP 架构与 tools/list·tools/call、评估（BFCL/ToolBench/τ-bench、Pass^k）、工具失败模式。week4 主线。
- [规范: Model Context Protocol (MCP) Specification 2025-06-18](https://modelcontextprotocol.io/specification/2025-06-18)
  Host/Client/Server 架构、JSON-RPC 2.0、Server 能力（Resources/Prompts/Tools）、Client 能力（Sampling/Roots/Elicitation）、生命周期（initialize→initialized→operation→shutdown）、能力协商、tools/list 与 tools/call 报文、安全原则（用户同意/工具安全/采样控制）。lecture04 第 35-36 课主线。
- [论文: Toolformer — Schick et al. (2023)](https://arxiv.org/abs/2302.04761) LM 自学调用 API（自监督 + 损失过滤）。lecture04 p22-31。
- [论文: Gorilla — Patil et al. (2023)](https://arxiv.org/abs/2305.15334) 1.6k API 微调 + 检索感知训练 + AST 匹配测幻觉。lecture04 p40-44。
- [论文: ToolLLM / ToolBench — Qin et al. (2023)](https://arxiv.org/abs/2307.16789) 16k 真实 API + 神经 API 检索器（ToolLLaMA）。lecture04 p37-38, p61-62。
- [论文: ToolkenGPT — Hao et al. (2024)](https://arxiv.org/abs/2305.11554) 把工具表示成 token（toolken）学 embedding。lecture04 p32-35。
- [基准: BFCL (Patil et al., 2025) / τ-bench (Yao et al., 2024, Pass^k)](https://gorilla.cs.berkeley.edu/leaderboard.html) 函数调用评估；τ-bench 用 Pass^k 衡量可靠性/一致性。lecture04 p58-66。

## Knowledge — Lecture05（Frameworks & Orchestration，源文件夹 week3-10.7）

- [课件: Stanford CS 329Z Lecture 5 "Frameworks & Orchestration" — Diyi Yang, Michael Ryan, John Yang](http://web.stanford.edu/class/cs329z)
  本地副本: week3-10.7/lecture05.pdf（132 页）。涵盖：三支柱 Data/System/Eval、框架谱系（模型→workflow→agent）、DSPy（签名/模块/优化器/编译器）、LangGraph（State/Node/Edge/条件边）、开源 agent harness（Mini SWE-Agent/OpenHands/Pi/OpenClaw）、编排与遥测（Temporal 持久执行 + MLflow/LangSmith/LangFuse）、最佳实践（简单/可观察可恢复/跑评估/懂底层）。lecture05 主线。
- [论文: DSPy — Compiling Declarative Language Model Calls into Self-Improving Pipelines — Khattab et al.](https://arxiv.org/abs/2310.03714)
  把 LM pipeline 抽象为文本变换图、声明式模块可参数化学习、编译器按指标优化；几行 DSPy 编译数分钟即使 GPT-3.5/llama2-13b 超过标准 few-shot（+25%/+65%）。本地: week3-10.7/…pdf。lecture05 第 40 课主线。
- [框架: LangGraph](https://langchain-ai.github.io/langgraph/) State/Node/Edge 图编排（含 create_agent）。lecture05 p52-77。
- [工具: Temporal](https://temporal.io/) Durable execution（Activity/Workflow/重试/服务端编排）。lecture05 p95-117。
- [工具: MLflow / LangSmith / LangFuse] 可观测性与追踪。lecture05 p119-121。
- [开源 harness: Mini SWE-Agent / OpenHands / Pi / OpenClaw] 不同设计取舍（工具/历史/权限/记忆）。lecture05 p82-85。

## Wisdom（社区）

- [r/LocalLLaMA](https://reddit.com/r/LocalLLaMA) 本地模型/智能体实践的高信号社区。
- [Hugging Face Agents 课程/论坛](https://huggingface.co/learn/agents-course) 教学性社区，交互练习智能体。
- DeepLearning.AI 短课(与 The Batch 同源)，可做实操补充。

## Gaps

- week1 之后(CS 329Z week2-5)：检索增强细分、函数调用、智能体记忆实现、多智能体系统、评估与护栏、编码智能体、主动式智能体——后续按学习进度补资料。
- 暂无明确的"智能体可靠性工程"权威教程(课件仅点到 HAL Dashboard / HarnessAudit)；可后期补。

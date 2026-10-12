# 0005 — 教学空间新增 Week3（CS329Z Lecture 3: RAG + Agents）

用户要求：根据 `C:\Users\nin\Desktop\hermes\agent\week3` 生成 lecture03 的课程。

## 输入材料
- week3/lecture03.pdf（63 页，CS329Z "RAG + Agents"）：Why RAG → RAG 管线 → 索引（分块/向量检索）→ 上下文检索 → 检索器（BM25/DPR/ColBERT）→ 混合检索与指标 → Agentic RAG（Self-RAG/CRAG/Search-R1）→ 失败模式。
- week3/Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks.pdf（RAG 原始论文, Lewis et al. 2021, 19 页）。
- week3/ColBERT …Late Interaction over BERT.pdf（Khattab & Zaharia, SIGIR 2020, 10 页）。

## 做了什么
新增 **lecture03 8 课**（编号 0023–0030，命名自带 `lecture03-` 来源前缀）：
- 0023 为什么需要检索：RAG 管线与两部件（p10-21 + RAG 论文）
- 0024 索引与分块：检索基本单位（p23-25, p36-38）
- 0025 上下文检索：Contextual Retrieval / Late Chunking / RAPTOR（p26-35）
- 0026 检索器：BM25 与 DPR（p40-48 + DPR 论文）
- 0027 ColBERT：晚期交互 / MaxSim（p50-54 + ColBERT 论文）
- 0028 混合检索、RRF 与检索指标（p45-46, p49）
- 0029 Agentic RAG：Self-RAG/CRAG/Search-R1（p56-61）
- 0030 RAG 失败模式全景（p63，Week3 收官）

同步更新：index.html（新增 Week3 路线表 + 8 条课时 + 标题/meta 改 1+2+3）、RESOURCES.md（Week3 一节，含两篇论文与 Anthropic Contextual Retrieval）、
reference/glossary.md（Week3 术语 25 条）、NOTES.md、本学习记录。

## 关于 lecture03 的 PDF 图表
本讲**绝大多数页是导入位图**（63 页里 33 页 raster、26 页 mixed、仅 4 页 native 矢量：p43/45/54/63）。
因此本批课程内容**全部基于文本层 + 公式页**（如 p41 BM25 公式、p45-46 指标定义、p49 RRF、p54 检索器延迟表、p63 失败清单），
对位图页（如 ColBERT 架构图 p52、RAG 管线图 p14）**只引用其标题/图注文字，未臆造图形内容**。视觉通道当前不可用（404）。

## Evidence
用户原话：“根据 C:\Users\nin\Desktop\hermes\agent\week3，生成 lecture03 的课程”。模型：本会话默认 deepseek-chat（provider: deepseek）。

## Implications
- 现在教学空间共 30 课，覆盖 CS329Z Lecture 1–3。Week3 的 RAG 细节可反哺 MISSION：用户要搭的 SGRT 检索/排查系统，正对应本讲的混合检索 + 指标 + 失败清单。
- 下周预告（课件路径）：函数调用 / 工具使用 → 可继续 `lecture04-*`。

## Status
active（Week3 8 课已交付；链接校验 + 浏览器冒烟通过）

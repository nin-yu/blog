# 0007 — 教学空间新增 Lecture05（Frameworks & Orchestration）+ 全部课页脚加"来源文件夹"标注

用户要求：根据 `C:\Users\nin\Desktop\hermes\agent\week3-10.7` 生成 lecture5 讲课内容；并按"每个 lecture 的文件夹名（如 week3-10.7）"更新前缀。

## 前缀的处理（用户明确选择）
用户在选项中选择：**保持 lecture01..lecture05 前缀不变，改为在每课页内标注"来源文件夹"**（不重命名文件）。
- 已给全部 44 课页脚加"来源文件夹：weekX-Y.Z"（lecture01–05 各对应见下）。
- 文件名保持稳定（index 与课间链接零改动）。

### 来源文件夹映射（关键发现）
`week1/ week2/ week3/` 三个旧文件夹**现在是空的**，PDF 都在带日期的文件夹里：
| 前缀 | 源文件夹 | 课件 |
| --- | --- | --- |
| lecture01 | week1-9.23/slides/ | lecture01.pdf |
| lecture02 | week2-9.28/ | lecture02.pdf |
| lecture03 | week2-9.30/ | lecture03.pdf |
| lecture04 | week3-10.5/ | lecture04.pdf |
| lecture05 | week3-10.7/ | lecture05.pdf |
注：此前把 lecture03 归为"week3"是错的，实际是 week2-9.30（RAG 那讲）。本次已按真实文件夹名全部改正。

## 输入材料
- week3-10.7/lecture05.pdf（132 页，CS329Z "Frameworks & Orchestration"）：三支柱 Data/System/Eval → 框架谱系 → DSPy → LangGraph → 开源 harness → 编排与遥测（Temporal）→ 最佳实践。
- week3-10.7/DSPy 论文（Khattab et al., 32 页）。

## 做了什么
新增 **lecture05 6 课**（编号 0039–0044，`lecture05-` 前缀）：
- 0039 什么叫"工程化"Agent：三支柱与框架谱系（p4-18）
- 0040 DSPy：签名/模块/优化器（p21-51 + DSPy 论文）
- 0041 LangGraph：State/Node/Edge（p52-77）
- 0042 开源 Agent Harness 对比（p78-89）
- 0043 编排与可观测性：Temporal / LangSmith / LangFuse（p90-122）
- 0044 工程最佳实践与挑战（p123-132，Lecture05 收官）

同步更新：index.html（Lecture05 路线表 + 6 条课时 + 标题/meta）、RESOURCES.md（Lecture05 一节）、glossary.md（Lecture05 术语 20 条）、NOTES.md（含来源文件夹映射）、本学习记录。

## 关于 lecture05 的 PDF 图表
lecture05 大量是**代码演示位图**（Signatures/Modules/Optimizers/Graph 的截图）。内容基于**文字页**（p21-22 DSPy 三件套、p51 DSPy Summary、p76 LangGraph Summary、p13/p122/p125/p129/p130 等）与 DSPy 论文摘要；代码细节未臆造。

## Evidence
用户原话："根据C:\Users\nin\Desktop\hermes\agent\week3-10.7里的内容生成下lecture5的讲课内容，然后根据每个lecture的文件夹名也就是week3-10.7这样的格式更新下前缀"。随后在澄清问题中选择"保持 lecture01..lecture05 前缀不变，只在每个 lesson 页内标注'来源文件夹'"。模型：本会话默认 deepseek-chat（provider: deepseek）。

## Implications
- 教学空间现共 44 课，覆盖 CS329Z Lecture 1–5。
- 以后新增课：文件名前缀仍用 lectureNN；页脚加"来源文件夹"标注（先 find lectureNN.pdf 定位文件夹）。
- 下一步仍可推进 MISSION 毕业考核（综合题 .md 作答 → 评卷）。

## Status
active（Lecture05 6 课已交付 + 全 44 课来源标注；链接校验 + 浏览器冒烟通过）

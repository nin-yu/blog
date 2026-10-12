# 0006 — 教学空间新增 Lecture04（CS329Z "Tool Use" + MCP 规范）

用户要求：看 `C:\Users\nin\Desktop\hermes\agent\week3-10.5` 与 MCP 规范 2025-06-18，生成 lecture04 的教学空间。

## 输入材料
- week3-10.5/lecture04.pdf（68 页，CS329Z "Tool Use"）：RAG 收尾 → Why tools → What are tools → Toolformer → Gorilla/ToolLLM/ToolkenGPT → 标准接口三代（REST/函数调用/MCP）→ 评估（BFCL/ToolBench/τ-bench）→ 失败模式。注意：文件夹名是 week3-10.5（补课/加课），但内容是第 4 讲。
- MCP 规范 2025-06-18（modelcontextprotocol.io）：overview / architecture / server/tools / basic/lifecycle 四个子页。

## 做了什么
新增 **lecture04 8 课**（编号 0031–0038，`lecture04-` 前缀）：
- 0031 RAG 收尾与"为什么要工具"（p4-17）
- 0032 什么是工具 + Toolformer（p18-31）
- 0033 规模化用工具：Gorilla / ToolLLM / ToolkenGPT（p32-45）
- 0034 标准接口三代：REST / 函数调用 / MCP（p47-56）
- 0035 MCP 深入：架构、tools/list 与 tools/call（MCP 规范 + p51-56）
- 0036 MCP 实战：把 REST 包装成 MCP 工具（p55-56 FastMCP 原码）
- 0037 评估工具使用：BFCL / ToolBench / τ-bench + Pass^k（p58-66）
- 0038 工具调用的失败模式（p67-68，Lecture04 收官）

同步更新：index.html（新增 Week4 路线表 + 8 条课时 + 标题/meta 改 1–4）、RESOURCES.md（Week4 一节，含 MCP 规范与 Toolformer/Gorilla/ToolLLM/ToolkenGPT/BFCL/τ-bench）、
reference/glossary.md（Week4 术语 22 条）、NOTES.md、本学习记录。

## 关于 lecture04 的 PDF 图表
lecture04 **以导入位图为主**（68 页里 39 raster、24 mixed、仅 5 native 矢量）。因此内容基于**文本层 + 代码页**（p55-56 的 FastMCP/from_openapi 与入站/出站鉴权是纯文本原码，可精确读取），
MCP 架构/协议细节**取自 MCP 规范原文**（而非课件位图）。位图页只引用其标题/文字，未臆造图形。视觉通道仍不可用（404）。

## Evidence
用户原话：“看下 C:\Users\nin\Desktop\hermes\agent\week3-10.5 和 [MCP 规范链接]，生成 lecture04 的教学空间”。模型：本会话默认 deepseek-chat（provider: deepseek）。

## Implications
- 教学空间现共 38 课，覆盖 CS329Z Lecture 1–4。Lecture04 的 MCP 内容与用户的实际需求（设备 API 包装、权限隔离、人审）高度对口，可作为 MISSION 里"故障排查 agent"的工具层实现参考。
- 与 Week1-0009（工具调用四步 + MCP 概念）、Week1-0012（判定范式）形成呼应：本讲把 MCP 从"概念"下沉到"协议细节 + 代码"。

## Status
active（Lecture04 8 课已交付；链接校验 + 浏览器冒烟通过）

# NOTES.md

教学偏好（从用户画像与历次对话整理，供教学设计参考）：

- 语言：中文讲解。
- 结构：先概念/原理，再细节，直接给结论；默认不用类比（明确要求"费曼方式"时才用直觉类比+逐层因果链）。工程桥（用用户熟悉的 ICP/门控/标定做对应）不算类比，是他偏好的锚点。
- 指标/数值要求：大白话解释含义 + 对工程的实质影响（精度/速度/成本），给具体数字。
- 自测形式：判断/选择均可，附答案与解析；**答案默认折叠**（HTML `<details>`），逼"先答后看"。
- 学习铁律：**覆盖≠领会**（学习记录 0001）。用户写过完整笔记 ≠ 概念吃透；领会证据 = 他自己的作答。所以 v2 重建把"workflow vs agent 判定"从第 1 课移到第 12 课毕业位，概念课全部前置。
- 综合题用 **Markdown 作答制**：每题一个 .md，作答区就在题目下（用户明确要求，方便记录与复盘）。评卷时我按每题末尾"评判关注点"逐条对。
- 用户背景：机器人/工业视觉/结构光/医学图像工程师（SGRT 放疗表面追踪），工程实现导向；agent 设计零基础。
- 教学空间：/mnt/c/Users/nin/Desktop/hermes/agent/teaching/（2026-10-09 用 deepseek-flash=DeepSeek-V4.1-Flash 重生成 v3；旧版存档 lessons-glm53-old/ 与 lessons-v4-old/ 保留）。
- Week2（2026-10-09 新增）：课程来源=lecture02.pdf（CS329Z "LLMs for Builders"）+ Anthropic《Building effective agents》《Effective context engineering》。文件名前缀标来源：lecture01-*=第1讲、lecture02-*=第2讲；Week1 旧 13 课已改名加 lecture01- 前缀（备份 lessons-preprename-backup/）。改名前务必备份、改后务必同步 index+课间链接。
- 阅读 PDF 图表：本机 aux 视觉模型常不可用（404）。lecture02 约 77 页为原生矢量图（文本层+坐标可精确读），约 79 页为导入位图（需视觉/OCR）。引用图内容前先判类型，勿臆造位图。
- Week3（2026-10-09 新增）：课程来源=lecture03.pdf（CS329Z "RAG + Agents"）+ RAG 原始论文 + ColBERT 论文。新增 lesson 0023-0030（`lecture03-*` 前缀）。lecture03 绝大多数页是导入位图（63 页中 33 raster / 26 mixed / 仅 4 native），内容全部基于文本层+公式页，位图只引标题未臆造。
- Week4（2026-10-09 新增）：课程来源=week3-10.5/lecture04.pdf（CS329Z "Tool Use"）+ MCP 规范 2025-06-18。新增 lesson 0031-0038（`lecture04-*` 前缀）。lecture04 同样以位图为主（68 页中 39 raster / 24 mixed / 5 native），内容基于文本层+代码页（含 p55-56 的 FastMCP 原码）。MCP 细节取自规范子页（architecture/tools/lifecycle）。
- Lecture05（2026-10-09 新增）：课程来源=week3-10.7/lecture05.pdf（CS329Z "Frameworks & Orchestration"）+ DSPy 论文。新增 lesson 0039-0044（`lecture05-*` 前缀）。lecture05 多为位图（代码演示页），内容基于文本层+p21-22/p51/p76 等文字页。
- **来源文件夹映射（重要）**：lecture01=week1-9.23/slides、lecture02=week2-9.28、lecture03=week2-9.30、lecture04=week3-10.5、lecture05=week3-10.7。用户要求：lesson 前缀保持 lectureNN 不变，改为**在每课页脚标注"来源文件夹"**（已全部 44 课加注）。注意 week1/week2/week3 三个旧文件夹已空，PDF 都在带日期的文件夹里。以后新增课：先 find 定位 lectureNN.pdf 所在文件夹，再把文件夹名写进页脚。
- **综合结业考试题（每讲一道，2026-10-09 新增）**：`综合题/结业考试-LectureNN-*.md`（5 道），各讲最后一课底部有入口块；格式=题目+「我的作答」+「评判关注点」。Lecture01 另保留早期 6 道专项题。以后新增讲：同法补一道结业考试 + 在最后一课加入口块 + 更新 综合题/README 与 index。
- **综合题目录结构（2026-10-09 重组）**：按讲分子文件夹 `综合题/Lecture01/ … Lecture05/`。每讲放 1 道结业考试；Lecture01 的 6 道早期专项题也归入 `Lecture01/`。新增讲：在对应 `LectureNN/` 放结业考试，并同步该讲最后一课入口块 + index + README。注意：`lessons-preprename-backup/` 是改名前的冻结归档，其内部链接已失效且**不维护**（用户要求保留存档）。

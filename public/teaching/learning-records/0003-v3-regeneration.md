# 0003 — 教学空间 v3：用 deepseek-flash（DeepSeek-V4.1-Flash）重生成 13 课

用户要求“用当前模型重写全部 13 课，旧版另存备份”。本次为 v3 再生成，课程结构与教学法不变（概念先行、判定课殿后、折叠式自测、综合题 Markdown 作答制），仅更换生成模型并重写正文。

## 做了什么
1. 归档旧版：`lessons - glm53` → `lessons-glm53-old/`（与生成前的 lessons/ 逐字节相同）。加上既有 `lessons-v4-old/`，现有两份存档。
2. 用第 5 课教学空间重写全部 13 课（0001–0013），保持同名文件与内部链接不变，故 index.html 无需改链接。
3. 每课统一：结论先行（takeaway）、原理、SGRT 工程桥、折叠式自测（`<details><summary>` 先答后看）、课间导航（footnav）。
4. index.html meta 标注 “重建版 v3（DeepSeek-V4.1-Flash 重生成）”，footer 列出两份存档。
5. 校验：14 个 HTML 的内部 href/src 全部存在（0 缺失）；浏览器冒烟通过（lesson.css 加载、body 底色 #f5f6f8、summary 为强调蓝 #1a73e8、details 默认折叠可展开）。

## Evidence
用户原话：“更新下 C:\Users\nin\Desktop\hermes\agent\teaching 中的教学空间的课程”，并在选项中选择“用当前模型(deepseek-flash/V4.1)重写全部13课，旧版另存备份”。模型：本会话默认 deepseek-flash（provider: deepseek 官方）。

## Implications
- 下一步仍是 MISSION 的毕业考核：用户在 `综合题/`（6 道 .md）用 Markdown 作答 → 我按每题“评判关注点”评卷 → 结论写入新的 learning-record 作为“领会证据”。
- 通过后进入 MISSION Success 2：从“日常 QA workflow”起步，亲手搭最小可评估版本。
- 三份课版可作 diff 材料，对比同一结构在不同模型下的讲法差异（后续若要研究“模型对教学效果的影响”可用）。

## Status
active（v3 已交付并校验通过；等待用户作答综合题）

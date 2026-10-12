# 0009 — 综合题/ 重组为按讲子文件夹（Lecture01–05）

用户要求：把专项题也放进"结业考试"体系、方便统一管理。经确认选择 **B：按讲建子文件夹**。

## 新结构
```
综合题/
├─ README.md                （总览：每讲结业考试 5 道 + Lecture01 专项 6 道）
├─ Lecture01/  结业考试-Lecture01-系统全设计.md + 01~06 专项题（6 道）
├─ Lecture02/  结业考试-Lecture02-上下文与选型.md
├─ Lecture03/  结业考试-Lecture03-RAG全链路.md
├─ Lecture04/  结业考试-Lecture04-工具与MCP.md
└─ Lecture05/  结业考试-Lecture05-工程化.md
```

## 做了什么
1. 新建 `Lecture01/ … Lecture05/`，把 5 道结业考试 + Lecture01 的 6 道专项题（01–06）移入对应文件夹。
2. 同步更新所有引用：
   - 5 讲最后一课的"综合结业考试题"入口链接 → `../综合题/LectureNN/…`
   - `lecture01-0013` 对 6 道专项题的链接 → `../综合题/Lecture01/…`
   - `index.html` 的 5 条结业考试链接
   - `综合题/README.md` 全部链接（改为带子目录 + 新增"目录结构"代码块）
3. 重写 `综合题/README.md`：新增目录结构说明；保留"每讲结业考试 + Lecture01 专项"两节；补充"新增一讲怎么放"的约定。

## 验证
- 活工作区（排除 lessons-preprename-backup/ 归档）45 个 HTML：0 缺失；所有 .md 目标（含子目录）均可解析。
- 唯一"missing"来自 `lessons-preprename-backup/0013-*.html`——那是改名前的冻结归档，保留旧链接是设计使然，不属于活工作区。
- 浏览器冒烟：index 的 综合题 链接全部指向 `综合题/LectureNN/…`；lesson.css 加载、底色 #f5f6f8 正常。

## 备注
`lessons-preprename-backup/` 是历史归档（v3→加 lecture 前缀之前），**不维护链接**。若日后想清掉它，需用户明确同意（用户此前要求保留存档）。

## Status
active

---
title: 'SGRT 光学体表引导放疗：为什么精度能到 0.5mm'
description: '从结构光重建到实时配准，拆解光学体表追踪系统的精度来源'
pubDate: '2026-10-11'
---

光学体表引导放疗（Surface-Guided Radiation Therapy, SGRT）的核心卖点，是**无标记、无电离辐射**的实时体位监测。但真正卡住临床落地的是精度——0.5mm 级的体表重建与配准误差。

## 精度从哪来

一套 SGRT 系统的误差链大致分三段：

1. **结构光重建误差** —— 相机标定精度、点云配准、体表缺失区域的插值
2. **体表到靶区的映射误差** —— 体表 ≠ 靶区，呼吸/摆位带来的形变
3. **实时追踪误差** —— 帧率、延迟、抖动过滤

第一段是工程能直接优化的，也是标定环节的重灾区。

## 标定：闭环是关键

传统标定靠人工反复调，费时且依赖经验。闭环标定的思路是：

- 机械臂携带标定板 → 6DOF 位姿调整
- 自动采集图像 → 计算重投影误差
- 误差 < 阈值则完成，否则优化参数（位姿 / 曝光）继续迭代

这样把"人调"变成"算法调"，标定一致性和可复现性都上来了。

## 代码骨架

以点云配准为例，核心是粗配准 + 精配准两段：

```python
import open3d as o3d

# 粗配准：FPFH + RANSAC
source = o3d.io.read_point_cloud("calib_board.ply")
target = o3d.io.read_point_cloud("scene.ply")

# 精配准：ICP
threshold = 1.0  # 单位与点云一致
trans_init = o3d.pipelines.registration.TransformationEstimationPointToPoint()
result = o3d.pipelines.registration.registration_icp(
    source, target, threshold, trans_init,
)
print(result.transformation)
print("fitness:", result.fitness)
```

## 小结

0.5mm 精度不是单一环节的功劳，而是重建、映射、追踪三段误差链协同控制的结果。工程上最值得投入的，是标定闭环——它决定了精度的上限和一致性。

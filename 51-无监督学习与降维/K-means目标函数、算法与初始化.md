---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第2页：K-means过程与缺点
keywords:
- machine-learning
- unsupervised-learning
- k-means
- clustering
---

# K-means目标函数、算法与初始化（★★★）

#machine-learning #unsupervised-learning #k-means #clustering

## Overview Table

| 项目 | 内容 |
|---|---|
| 目标 | 最小化簇内平方和 WCSS |
| 分配步 | 每个样本归入最近质心 |
| 更新步 | 质心取所属样本均值 |
| 停止 | 分配不变、中心变化小或达到迭代上限 |

## 目标函数

`J=Σ_i ||x_i-μ_{c_i}||²`

    initialize K centers
      → assign points to nearest center
      → recompute mean centers
      → repeat until convergence

每一步都不增加目标函数，因此有限分配下会收敛到局部最优。K-means++ 以距离平方加权选择初始中心，通常比纯随机初始化稳定。

## 适用边界

适合近似球状、尺度相近、以欧氏距离可表达相似性的簇。对异常值、尺度、非凸簇和密度差异敏感。

> [!warning]
> K-means 的“中心”是均值，不一定是数据点；它保证目标单调下降但不保证全局最优，通常需多次初始化。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 两个步骤 | 最近中心分配、按簇求均值 |
| 对尺度敏感 | 欧氏距离受量纲支配 |
| 改善初始化 | K-means++ 与多次重启 |

## Related Notes

- [[聚类评估、距离选择与K值确定]]
- [[GMM、EM与软聚类]]
- [[数据预处理、标准化与特征工程]]
- [[练习-无监督学习与降维]]
- [[34-机器学习高频易错点]]

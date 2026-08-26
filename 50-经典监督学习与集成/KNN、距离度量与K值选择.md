---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第3页：KNN
keywords:
- machine-learning
- supervised-learning
- knn
- distance-metrics
---

# KNN、距离度量与K值选择（★★★）

#machine-learning #supervised-learning #knn #distance-metrics

## Overview Table

| 组成 | 选择 |
|---|---|
| 邻居数 K | 小 K 方差高，大 K 偏差高 |
| 距离 | 欧氏、曼哈顿、余弦、马氏等 |
| 分类聚合 | 多数投票、距离加权投票 |
| 回归聚合 | 均值、中位数、距离加权均值 |

## 推断流程

    query x
      → compute distance to training samples
      → select K nearest
      → vote/average

KNN 是惰性、非参数方法：训练主要是存储数据，推断成本较高。特征尺度会直接影响距离，通常需标准化；高维中距离趋同会导致维数灾难。

## K值选择

用验证集或交叉验证选择 K。分类二元场景常取奇数减少平票，但多分类仍可能平票，需要明确规则。KD-tree 等索引在低维有效，高维常退化。

> [!warning]
> “非参数”不表示没有超参数，也不表示模型复杂度固定；K、距离、权重和特征表示都决定决策边界。

## Exam/Test Patterns

| 现象 | 原因/处理 |
|---|---|
| K 太小 | 对噪声敏感、高方差 |
| K 太大 | 边界过平滑、高偏差 |
| 量纲不同 | 先标准化或选合适距离 |

## Related Notes

- [[数据预处理、标准化与特征工程]]
- [[K-means目标函数、算法与初始化]]
- [[分类指标、ROC-AUC与阈值]]
- [[练习-经典监督学习与集成]]
- [[34-机器学习高频易错点]]

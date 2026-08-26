---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
- 【精品】计算机保研面试_数学常见题.pdf
- 6系2020年推免复试参考资料.pdf
part: 主资料第2-3页；数学题第4-6页；6系资料第20页
keywords:
- machine-learning
- unsupervised-learning
- pca
- dimensionality-reduction
---

# PCA、方差最大化与协方差矩阵（★★★）

#machine-learning #unsupervised-learning #pca #dimensionality-reduction

## Overview Table

| 步骤 | 操作 |
|---|---|
| 中心化 | `X_c=X-mean(X)` |
| 协方差 | `C=X_cᵀX_c/(n-1)` |
| 分解 | 求 C 的特征值与特征向量 |
| 选择 | 取最大 k 个特征值对应方向 |
| 投影 | `Z=X_c W_k` |

## 两个等价目标

PCA 的主方向既最大化投影方差，也在给定维数下最小化平方重构误差。解释方差比：

`ratio_j = λ_j / Σ_i λ_i`

    centered X → covariance/eigendecomposition
               → top eigenvectors Wk
               → low-dimensional Z=XWk

特征尺度差异大时通常先标准化，否则大方差量纲会主导主成分。

> [!warning]
> PCA 是线性、无监督降维，不使用标签；主成分符号可整体翻转而不改变子空间，成分也不必直接具有业务语义。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| PCA目标 | 最大投影方差 / 最小重构误差 |
| 是否要中心化 | 要，协方差方向相对均值定义 |
| 选维数 | 累计解释方差 + 下游验证 |

## Related Notes

- [[PCA、SVD与降维方法选择]]
- [[降维、特征选择与可视化边界]]
- [[线性回归与最小二乘法]]
- [[练习-无监督学习与降维]]
- [[34-机器学习高频易错点]]

---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
- 【精品】计算机保研面试_数学常见题.pdf
- 6系2020年推免复试参考资料.pdf
part: 主资料第2页；数学题第4-6页特征分解与SVD；6系资料第20页
keywords:
- machine-learning
- unsupervised-learning
- svd
- representation-learning
---

# PCA、SVD与降维方法选择（★★★）

#machine-learning #unsupervised-learning #pca #svd

## Overview Table

| 方法 | 线性 | 是否用标签 | 重点 |
|---|---|---|---|
| PCA/SVD | 是 | 否 | 全局最大方差低秩子空间 |
| LDA | 是 | 是 | 类间分离与类内紧凑 |
| t-SNE | 否 | 否 | 局部邻域可视化 |
| UMAP | 否 | 否 | 邻域图与流形结构 |
| Autoencoder | 通常否 | 自监督重构 | 学习非线性表示 |

## PCA与SVD

对中心化矩阵 `X=UΣVᵀ`，PCA 主方向是 V 的前 k 列；协方差特征值与奇异值平方成比例。直接对 X 做 SVD 常比显式构造协方差矩阵更稳定。

## 特征选择 vs 降维

特征选择保留原始维度子集，解释性强；降维创建新组合特征，压缩和去相关更强但语义可能弱。

> [!warning]
> t-SNE/UMAP 二维图中的簇间全局距离和簇大小不一定可信；任何降维器都必须只在训练集拟合，再应用到验证和测试集。

## Exam/Test Patterns

| 需求 | 方法 |
|---|---|
| 线性压缩/去相关 | PCA/SVD |
| 有标签线性判别 | LDA |
| 高维可视化 | t-SNE/UMAP，谨慎解释 |

## Related Notes

- [[PCA、方差最大化与协方差矩阵]]
- [[聚类评估、距离选择与K值确定]]
- [[数据泄漏、类别不平衡与分布偏移]]
- [[练习-无监督学习与降维]]
- [[34-机器学习高频易错点]]

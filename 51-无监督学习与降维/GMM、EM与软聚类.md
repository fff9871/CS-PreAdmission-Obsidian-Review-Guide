---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
- 【精品】计算机保研面试_数学常见题.pdf
part: 主资料第2、8页：GMM与生成式模型；数学题第7-10页概率基础
keywords:
- machine-learning
- unsupervised-learning
- gaussian-mixture
- em-algorithm
---

# GMM、EM与软聚类（★★★）

#machine-learning #unsupervised-learning #gaussian-mixture #em-algorithm

## Overview Table

| 模型 | 分配 | 簇形状 |
|---|---|---|
| K-means | 硬分配 | 近似球形、同尺度 |
| GMM | 后验责任度软分配 | 可用协方差表达椭球和方向 |

## 混合模型

`p(x)=Σ_k π_k N(x|μ_k,Σ_k)`

EM 交替：

1. **E-step**：用当前参数计算责任度 `γ_ik=p(z_i=k|x_i)`。
2. **M-step**：用责任度加权更新 `π_k, μ_k, Σ_k`。

    parameters → E: infer latent assignments
         ↑                         ↓
         └──── M: maximize expected log likelihood

EM 单调不降低观测数据似然，但和 K-means 一样可能停在局部最优，需要初始化和正则协方差。

> [!warning]
> GMM 的分量不必等同真实语义类别；若协方差塌缩到单点，似然可病态增大，需要最小方差、先验或约束。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 软聚类输出 | 每个样本属于各分量的后验概率 |
| E/M步骤 | 推断隐变量 / 更新参数 |
| K-means关系 | 可视为特定极限/简化的硬分配混合模型 |

## Related Notes

- [[K-means目标函数、算法与初始化]]
- [[判别式模型与生成式模型]]
- [[最大似然、MAP与贝叶斯公式]]
- [[练习-无监督学习与降维]]
- [[34-机器学习高频易错点]]

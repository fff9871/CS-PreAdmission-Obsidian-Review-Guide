---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第2页：K值、距离、归一化与异常值问题的扩展
keywords:
- machine-learning
- unsupervised-learning
- cluster-evaluation
- silhouette-score
---

# 聚类评估、距离选择与K值确定（★★★）

#machine-learning #unsupervised-learning #clustering #cluster-evaluation

## Overview Table

| 方法 | 依据 | 局限 |
|---|---|---|
| Elbow | WCSS 随 K 的拐点 | 拐点可能不明显 |
| Silhouette | 簇内紧密与簇间分离 | 对距离和簇形状敏感 |
| Gap Statistic | 与无结构参考分布比较 | 计算较重 |
| 外部指标 | ARI、NMI 等与真实标签比较 | 需要外部标签 |
| 稳定性 | 重采样后聚类一致性 | 成本高、需匹配簇标签 |

## 距离与数据类型

欧氏适合连续标准化特征；余弦关注方向而非模长；曼哈顿对坐标差累加；混合类型可用 Gower 等度量。距离选择实际定义了“相似”的含义。

## 评估流程

    domain goal → representation → distance
       → candidate K/algorithm
       → internal + stability + domain validation

聚类没有标签时不能只凭一个分数断言真实类别；需结合可解释性、下游任务和多次初始化稳定性。

> [!warning]
> WCSS 随 K 增大必然不增，单纯取最小值会选择最大 K；Silhouette 高也不保证业务上有意义。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 如何选 K | Elbow、Silhouette、稳定性和领域解释结合 |
| 文本方向相似 | 常用余弦距离/相似度 |
| 有真标签 | ARI/NMI 等外部指标 |

## Related Notes

- [[K-means目标函数、算法与初始化]]
- [[GMM、EM与软聚类]]
- [[降维、特征选择与可视化边界]]
- [[练习-无监督学习与降维]]
- [[34-机器学习高频易错点]]

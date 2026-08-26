---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第2页：监督学习中的集成学习；第10页：bagging防过拟合
keywords:
- machine-learning
- ensemble-learning
- bagging
- random-forest
---

# Bagging、随机森林与Boosting（★★★）

#machine-learning #supervised-learning #ensemble-learning #bagging #random-forest

## Overview Table

| 方法 | 基学习器关系 | 主要作用 |
|---|---|---|
| Bagging | Bootstrap 数据上并行训练 | 降低方差 |
| Random Forest | Bagging 树 + 每次分裂随机选特征 | 进一步去相关、稳健 |
| Boosting | 串行关注前轮错误/残差 | 降偏差，可形成强学习器 |
| Stacking | 元模型融合多个模型输出 | 学习组合规则 |

## Bagging 路径

    training set
      → bootstrap sample 1 → model 1 ┐
      → bootstrap sample 2 → model 2 ├→ vote/average
      → bootstrap sample B → model B ┘

随机森林中树尽量充分生长，同时用特征子采样降低树间相关性。袋外 OOB 样本可估计泛化误差和特征重要性。

> [!warning]
> Bagging 主要降方差，未必显著降低强偏差；随机森林的“随机”包含样本和特征随机性。基于 impurity 的特征重要性可能偏向高基数特征。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| Bagging 是否串行 | 否，可并行 |
| RF 比普通 Bagging 多什么 | 节点分裂时随机特征子集 |
| OOB | 未进入某棵树 bootstrap 的样本 |

## Related Notes

- [[ID3、C4.5、CART与剪枝]]
- [[AdaBoost、GBDT与XGBoost]]
- [[过拟合、欠拟合与偏差-方差]]
- [[练习-经典监督学习与集成]]
- [[34-机器学习高频易错点]]

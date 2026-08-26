---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第2页集成学习主题的教材级扩展
keywords:
- machine-learning
- ensemble-learning
- boosting
- gradient-boosting
---

# AdaBoost、GBDT与XGBoost（★★★）

#machine-learning #supervised-learning #ensemble-learning #boosting

## Overview Table

| 方法 | 每轮拟合对象 | 组合 |
|---|---|---|
| AdaBoost | 提高错分样本权重 | 加权投票 |
| GBDT | 当前损失的负梯度/伪残差 | 加法模型 |
| XGBoost | 一、二阶近似 + 树复杂度正则 | 正则化梯度提升树 |

## Gradient Boosting

    F₀(x)
      → compute pseudo-residuals
      → fit weak tree h₁
      → F₁=F₀+ηh₁
      → repeat

学习率 η 与树数存在权衡：较小学习率通常需更多树。树深、采样、列采样和正则共同控制容量。

## 对比随机森林

随机森林并行训练高方差树并平均，主要降方差；Boosting 串行修正当前模型，常更强但对噪声、超参数和训练时间更敏感。

> [!warning]
> GBDT 拟合的是损失函数的负梯度，平方损失时才直接等于普通残差；XGBoost 不只是“更快的 GBDT”，还加入二阶信息、正则和工程优化。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| AdaBoost 关注什么 | 前轮错分样本 |
| GBDT 每轮目标 | 当前损失的负梯度/伪残差 |
| RF vs Boosting | 并行平均降方差 vs 串行加法纠错 |

## Related Notes

- [[Bagging、随机森林与Boosting]]
- [[决策树、信息熵与信息增益]]
- [[BGD、SGD、Mini-batch与Momentum]]
- [[练习-经典监督学习与集成]]
- [[34-机器学习高频易错点]]

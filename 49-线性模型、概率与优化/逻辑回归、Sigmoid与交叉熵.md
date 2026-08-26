---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第4页：逻辑回归
keywords:
- machine-learning
- linear-models
- logistic-regression
- cross-entropy
---

# 逻辑回归、Sigmoid与交叉熵（★★★）

#machine-learning #linear-models #logistic-regression #cross-entropy

## Overview Table

| 对象 | 公式 |
|---|---|
| Logit | `z=wᵀx+b` |
| Sigmoid | `σ(z)=1/(1+e^-z)` |
| 概率 | `P(y=1|x)=σ(z)` |
| 二元交叉熵 | `-[y log p+(1-y)log(1-p)]` |
| 决策边界 | `wᵀx+b=log(τ/(1-τ))` |

## 为什么是线性分类器

Sigmoid 将线性分数映射到 `(0,1)`，但给定固定阈值后，输入空间中的决策边界仍是超平面。逻辑回归直接建模条件概率，训练通常是凸优化。

    x → linear logit z → sigmoid probability p → threshold/class

多分类可用 Softmax 回归；多标签则为每个标签独立使用 Sigmoid。

> [!warning]
> 逻辑回归不是“线性回归后随便接 Sigmoid”：其概率假设、对数似然和交叉熵目标是一体的。数值实现应使用 logits 版本损失，避免先显式 Sigmoid 再取 log 的溢出。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 为何叫回归 | 对 log-odds 做线性建模，但任务通常是分类 |
| 决策边界 | 输入空间中的线性超平面 |
| BCE来源 | Bernoulli 条件似然的负对数 |

## Related Notes

- [[线性回归与最小二乘法]]
- [[最大似然、MAP与贝叶斯公式]]
- [[分类指标、ROC-AUC与阈值]]
- [[练习-线性模型、概率与优化]]
- [[34-机器学习高频易错点]]

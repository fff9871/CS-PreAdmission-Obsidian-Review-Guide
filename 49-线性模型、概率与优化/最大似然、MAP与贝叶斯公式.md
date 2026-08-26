---
source_pdf:
- 【精品】计算机保研面试_数学常见题.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 数学题第7-10页；综合题第50、53页；主资料第3、8页相关概率模型
keywords:
- machine-learning
- probabilistic-learning
- maximum-likelihood
- bayes-rule
---

# 最大似然、MAP与贝叶斯公式（★★★）

#machine-learning #probabilistic-learning #maximum-likelihood #bayes-rule

## Overview Table

| 方法 | 优化对象 | 公式 |
|---|---|---|
| MLE | 数据似然 | `argmaxθ p(D|θ)` |
| MAP | 后验概率 | `argmaxθ p(D|θ)p(θ)` |
| 贝叶斯预测 | 积分参数不确定性 | `p(y|x,D)=∫p(y|x,θ)p(θ|D)dθ` |

## 贝叶斯公式

`p(θ|D)=p(D|θ)p(θ)/p(D)`

    prior p(θ)
       × likelihood p(D|θ)
       → posterior p(θ|D)

取负对数后，MAP 常表现为“数据损失 + 正则项”：高斯先验对应 L2，拉普拉斯先验对应 L1。

## 对数似然

独立样本似然是概率乘积，取 log 后变成求和，更易计算且最大点不变。分类交叉熵和回归 MSE 都可从具体噪声/分布假设推导。

> [!warning]
> `p(D|θ)` 是 θ 的函数但不是 θ 的概率分布；MAP 是后验众数的点估计，不等于完整贝叶斯推断。连续概率密度可以大于 1，概率由积分给出。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| MLE vs MAP | MAP 多了参数先验 |
| 为什么取 log | 乘积变求和、数值更稳定、最优点不变 |
| 正则与先验 | L2↔高斯，L1↔拉普拉斯 |

## Related Notes

- [[逻辑回归、Sigmoid与交叉熵]]
- [[朴素贝叶斯与条件独立假设]]
- [[L1、L2正则化与稀疏性]]
- [[练习-线性模型、概率与优化]]
- [[34-机器学习高频易错点]]

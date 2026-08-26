---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
part: 主资料第4-5页；综合题第40页梯度下降
keywords:
- machine-learning
- optimization
- gradient-descent
- momentum
---

# BGD、SGD、Mini-batch与Momentum（★★★）

#machine-learning #optimization #gradient-descent #momentum

## Overview Table

| 方法 | 每次梯度数据量 | 特点 |
|---|---:|---|
| BGD | 全训练集 | 梯度稳定，单步昂贵 |
| SGD | 1 个样本 | 噪声大、更新频繁 |
| Mini-batch SGD | B 个样本 | 向量化效率与噪声折中 |
| Momentum | 梯度的指数移动方向 | 加速一致方向、抑制震荡 |

## 更新公式

`θ_{t+1}=θ_t-η g_t`

Momentum 常写为：

`v_t=βv_{t-1}+(1-β)g_t`，`θ_{t+1}=θ_t-ηv_t`

    batch → forward → loss → backward gradient
                         ↓
                    optimizer step

Mini-batch 大小影响吞吐、显存、梯度噪声和 BatchNorm 统计；epoch 是完整遍历训练集一次，不等于固定更新次数。

> [!warning]
> SGD 的噪声不等于“只会陷入局部最优”；非凸优化中更常见的问题还包括鞍点、平坦区和泛化差异。batch 变大时学习率与训练步数不能机械不变。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 最适合 GPU 向量化 | Mini-batch/BGD |
| Momentum 作用 | 累积一致方向，降低狭长谷震荡 |
| epoch vs step | 一次全数据遍历 vs 一次参数更新 |

## Related Notes

- [[Adagrad、RMSprop与Adam]]
- [[牛顿法、拟牛顿法与学习率策略]]
- [[PyTorch训练循环、Loss与Optimizer]]
- [[练习-线性模型、概率与优化]]
- [[34-机器学习高频易错点]]

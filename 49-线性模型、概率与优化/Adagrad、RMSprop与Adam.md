---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第5-6页：自适应优化器
keywords:
- machine-learning
- optimization
- adaptive-optimizers
- adam
---

# Adagrad、RMSprop与Adam（★★★）

#machine-learning #optimization #adaptive-optimizers #adam

## Overview Table

| 优化器 | 状态 | 核心特点 |
|---|---|---|
| Adagrad | 累积梯度平方 | 稀疏特征友好，学习率持续衰减 |
| RMSprop | 梯度平方指数移动平均 | 避免分母无限累积 |
| Adam | 一阶矩 + 二阶矩 + 偏差修正 | 常用默认优化器，收敛快 |
| AdamW | 解耦权重衰减 | 更清晰实现 weight decay |

## 典型公式

`m_t=β1 m_{t-1}+(1-β1)g_t`

`v_t=β2 v_{t-1}+(1-β2)g_t²`

偏差修正后：`θ←θ-η m̂/(sqrt(v̂)+ε)`。

自适应方法按参数历史梯度尺度调整有效步长；它们可加快早期训练，但最终泛化不一定优于精心调节的 SGD + Momentum。

> [!warning]
> Adam 不是 RMSprop 与 Momentum 的简单相加口号：还有偏差修正和具体更新定义。`weight_decay` 在 Adam 和 AdamW 中的数学含义可不同。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| Adagrad 后期停滞 | 累积平方使有效学习率过小 |
| RMSprop 改进 | 用指数移动平均替代无限累加 |
| Adam 两个矩 | 梯度均值与梯度平方均值 |

## Related Notes

- [[BGD、SGD、Mini-batch与Momentum]]
- [[牛顿法、拟牛顿法与学习率策略]]
- [[L1、L2正则化与稀疏性]]
- [[练习-线性模型、概率与优化]]
- [[34-机器学习高频易错点]]

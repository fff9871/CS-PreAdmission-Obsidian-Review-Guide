---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第6、11、14页：BN、GN及训练测试差异
keywords:
- machine-learning
- deep-learning
- normalization
- batch-normalization
---

# 归一化：BatchNorm、LayerNorm、GroupNorm与InstanceNorm（★★★）

#machine-learning #deep-learning #normalization #batch-normalization

## Overview Table

| 方法 | 统计维度（常见NCHW） | 典型场景 |
|---|---|---|
| BatchNorm | 每通道跨 N,H,W | CNN、大 batch |
| LayerNorm | 每样本跨特征维 | Transformer、RNN |
| InstanceNorm | 每样本每通道跨 H,W | 风格迁移 |
| GroupNorm | 每样本按通道组跨 C/H/W | 小 batch 视觉模型 |

## BatchNorm

`x̂=(x-μ_B)/sqrt(σ_B²+ε)`，`y=γx̂+β`

训练时用当前 batch 统计并更新运行均值/方差；推理时使用冻结的运行统计。可学习参数通常是每通道 γ、β，共 `2C` 个。

    affine/conv → normalization → activation

这是常见顺序，但预激活 ResNet、Transformer 等架构可采用不同布局。

> [!warning]
> BN 不要求数据变成严格标准正态，只规范一二阶统计；小 batch 下统计噪声大。`eval()` 不会关闭梯度，只改变 BN/Dropout 等模块行为。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| BN训练/测试 | batch统计 vs running统计 |
| 小batch | GN/LN更稳定或冻结BN |
| BN参数数 | 通常2C个可学习γ、β |

## Related Notes

- [[梯度消失、梯度爆炸与参数初始化]]
- [[Dropout、早停与数据增强]]
- [[PyTorch的train-eval、BatchNorm与Dropout]]
- [[练习-神经网络训练与优化]]
- [[34-机器学习高频易错点]]

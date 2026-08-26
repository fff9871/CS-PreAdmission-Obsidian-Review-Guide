---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第10-12、14页：过拟合、Dropout与数据增强
keywords:
- machine-learning
- deep-learning
- dropout
- data-augmentation
---

# Dropout、早停与数据增强（★★★）

#machine-learning #deep-learning #dropout #data-augmentation

## Overview Table

| 方法 | 训练时 | 推理时 |
|---|---|---|
| Inverted Dropout | 按概率置0并除以保留率 | 恒等映射 |
| 早停 | 监控验证指标并保存最佳点 | 使用最佳检查点 |
| 数据增强 | 随机生成保标签变换 | 通常使用确定性预处理，可选TTA |

## Dropout

保留率 `q=1-p`：训练时 `y=m⊙x/q, m~Bernoulli(q)`，使输出期望与推理时一致。它降低单元共适应，近似组合多个子网络。

## 数据增强

图像可翻转、裁剪、颜色扰动、噪声、Mixup/CutMix；变换必须尽量保持任务标签。例如数字识别中任意旋转可能改变语义。

## 早停

以验证集指标为准设置 patience，保存最佳权重；它既是训练控制，也是隐式正则化。

> [!warning]
> Dropout 推理时应关闭，但 Monte Carlo Dropout 是刻意保留随机性的特殊不确定性方法。BN 与 Dropout 都会改变训练/推理行为，却不能互相替代。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| Dropout为何除以1-p | 保持训练与推理输出期望一致 |
| 早停看什么 | 验证指标，不是训练loss |
| 增强原则 | 保持标签语义且只用于训练流水线 |

## Related Notes

- [[过拟合、欠拟合与偏差-方差]]
- [[L1、L2正则化与稀疏性]]
- [[归一化：BatchNorm、LayerNorm、GroupNorm与InstanceNorm]]
- [[练习-神经网络训练与优化]]
- [[34-机器学习高频易错点]]

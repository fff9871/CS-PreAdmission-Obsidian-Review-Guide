---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第13页：怎么看loss和acc变化
keywords:
- machine-learning
- pytorch
- learning-curves
- debugging
---

# Loss与Accuracy曲线诊断（★★★）

#machine-learning #pytorch #learning-curves #debugging

## Overview Table

| 曲线 | 常见解释 | 下一步 |
|---|---|---|
| train/val loss都降 | 正常学习 | 继续至验证饱和 |
| train降、val先降后升 | 过拟合 | 早停、正则、增强 |
| 两者都高且平 | 欠拟合/优化失败 | tiny-batch测试、容量/学习率检查 |
| loss震荡 | 学习率、batch或数据噪声 | 降LR、查归一化/梯度 |
| acc高、loss升 | 少数高置信错误 | 看校准、混淆矩阵和样本 |

## 诊断层次

    1 data shape/label/range
    2 forward and loss definition
    3 gradient existence and scale
    4 optimizer and learning rate
    5 evaluation mode and metric
    6 generalization/distribution

先尝试过拟合一个极小 batch：若失败，多为实现、数据或容量问题；若成功，再研究泛化。

## 记录原则

区分 batch loss 与 epoch平均；同时记录学习率、梯度范数、吞吐、显存和每类指标。比较实验应固定数据划分和随机性。

> [!warning]
> Accuracy 是离散阈值结果，loss 还反映置信度，因此两者可以不同步；单条曲线不能唯一定位原因。

## Exam/Test Patterns

| 症状 | 检查 |
|---|---|
| loss降acc不变 | 阈值附近尚未翻类、类别不平衡或指标bug |
| val每次不同 | eval模式、随机增强、采样和种子 |
| 训练极慢 | DataLoader、设备、同步点、batch与算子 |

## Related Notes

- [[超参数、学习率调度与训练诊断]]
- [[PyTorch的train-eval、BatchNorm与Dropout]]
- [[数据泄漏、类别不平衡与分布偏移]]
- [[练习-PyTorch与训练实践]]
- [[34-机器学习高频易错点]]

---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第7、13页：残差连接、训练ResNet
keywords:
- machine-learning
- computer-vision
- resnet
- transfer-learning
---

# ResNet、残差块与迁移学习（★★★）

#machine-learning #computer-vision #resnet #transfer-learning

## Overview Table

| 策略 | 做法 | 适用 |
|---|---|---|
| Feature extraction | 冻结 backbone，只训练新 head | 数据少、领域接近 |
| Partial fine-tuning | 解冻后几层 | 中等域差异 |
| Full fine-tuning | 全模型小学习率训练 | 数据较多或域差异大 |

## 残差块

Basic block 常用两个 3×3；Bottleneck 常用 `1×1降维→3×3→1×1升维`。空间或通道变化时 shortcut 使用投影。

## 迁移学习流程

    load pretrained weights
      → replace classification head
      → train head
      → optionally unfreeze backbone gradually
      → validate and save best checkpoint

输入归一化应与预训练权重匹配；小 batch 微调时要特别处理 BN 统计和冻结策略。

> [!warning]
> “冻结参数”与 `eval()` 不等价：前者控制梯度，后者控制 BN/Dropout 行为。加载预训练权重后仍需验证类别映射和输入预处理。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 小数据迁移 | 冻结backbone，训练head起步 |
| 解冻后学习率 | 通常比新head更小 |
| BN小batch | 冻结统计或使用替代归一化 |

## Related Notes

- [[残差连接、退化问题与深层网络]]
- [[PyTorch的模型、参数与前向传播]]
- [[Vision Transformer、Patch与位置编码]]
- [[练习-CNN与视觉模型]]
- [[34-机器学习高频易错点]]

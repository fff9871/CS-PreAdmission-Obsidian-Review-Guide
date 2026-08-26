---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第10页：Transformer与多头注意力
keywords:
- machine-learning
- sequence-models
- attention
- query-key-value
---

# Attention与Query-Key-Value（★★★）

#machine-learning #sequence-models #attention #query-key-value

## Overview Table

| 对象 | 直觉 |
|---|---|
| Query Q | 当前需要检索什么 |
| Key K | 每个位置可被匹配的索引 |
| Value V | 匹配后实际汇聚的内容 |

## 缩放点积注意力

`Attention(Q,K,V)=softmax(QKᵀ/√d_k)V`

    query
      → similarity with all keys
      → scale + mask + softmax weights
      → weighted sum of values

除以 `√d_k` 可防止维度增大时点积方差过大、Softmax 过度饱和。Mask 可屏蔽 padding 或未来位置。

## Cross vs Self

Self-Attention 的 Q/K/V 来自同一序列；Cross-Attention 的 Query 来自一个序列，Key/Value 来自另一个上下文。

> [!warning]
> 注意力权重是模型内部匹配分布，不应无条件解释为因果贡献；Q、K、V 是学习投影后的表示，不是固定语义标签。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 为什么除√dk | 控制点积分布尺度，避免Softmax饱和 |
| Padding mask | 不让模型关注填充位置 |
| Cross-Attention | Q与K/V来自不同来源 |

## Related Notes

- [[Self-Attention与Multi-Head Attention]]
- [[Transformer编码器、解码器、Mask与位置编码]]
- [[Vision Transformer、Patch与位置编码]]
- [[练习-序列模型、注意力与Transformer]]
- [[34-机器学习高频易错点]]

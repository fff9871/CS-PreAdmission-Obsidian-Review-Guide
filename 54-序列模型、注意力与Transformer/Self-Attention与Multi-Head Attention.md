---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第10页：为什么需要Multi-head Attention
keywords:
- machine-learning
- sequence-models
- self-attention
- multi-head-attention
---

# Self-Attention与Multi-Head Attention（★★★）

#machine-learning #sequence-models #self-attention #multi-head-attention

## Overview Table

| 单头 | 多头 |
|---|---|
| 一组Q/K/V投影 | h组不同投影子空间 |
| 一种匹配模式 | 可并行捕捉不同关系/位置模式 |
| 输出一个聚合 | 拼接各头后线性映射 |

## 公式

`head_i=Attention(QW_i^Q, KW_i^K, VW_i^V)`

`MHA=Concat(head_1,...,head_h)W^O`

在总模型维度固定时，每头维度通常为 `d_model/h`，多头并不必然把核心投影参数量乘 h，而是重新分配子空间。

## 自注意力特点

任意两个 token 一层即可交互，长程依赖路径短，序列维训练可并行；标准实现的注意力矩阵时间/显存为 `O(n²)`。

> [!warning]
> 多头不保证每个头自动学到人类可命名的不同语义，也不是头数越多越好；每头维度过小、冗余头和计算预算都会限制效果。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 多头价值 | 在不同表示子空间并行学习多种关系 |
| 长程依赖 | 任意位置直接交互，路径短 |
| 主要瓶颈 | 长序列下N×N注意力矩阵 |

## Related Notes

- [[Attention与Query-Key-Value]]
- [[Transformer编码器、解码器、Mask与位置编码]]
- [[Vision Transformer、Patch与位置编码]]
- [[练习-序列模型、注意力与Transformer]]
- [[34-机器学习高频易错点]]

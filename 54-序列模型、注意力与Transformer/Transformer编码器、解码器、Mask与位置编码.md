---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第8、10页：ViT、Transformer与多头注意力
keywords:
- machine-learning
- sequence-models
- transformer
- positional-encoding
---

# Transformer编码器、解码器、Mask与位置编码（★★★）

#machine-learning #sequence-models #transformer #positional-encoding

## Overview Table

| 组件 | Encoder | Decoder |
|---|---|---|
| Self-Attention | 双向或按任务mask | 因果mask |
| Cross-Attention | 通常无 | 读取encoder输出 |
| FFN | 每位置共享两层MLP | 同样 |
| Residual + Norm | 每子层使用 | 每子层使用 |

## 编码器块

    tokens + positions
      → self-attention → residual/norm
      → feed-forward → residual/norm

解码器自回归训练用 causal mask 阻止位置 t 看见未来 token；padding mask 屏蔽无效位置。

## 位置编码

Self-Attention 本身对 token 排列缺少顺序感，需要绝对、相对、旋转等位置编码。序列外推能力依编码形式和训练分布。

## 复杂度

标准注意力为 `O(n²d)`，RNN 单层为 `O(nd²)` 但时间步串行；谁更快取决于序列长度、维度、并行硬件和实现。

> [!warning]
> Transformer 不等于只有 Attention：还包含 FFN、残差、归一化、位置表示和任务头。训练时 Teacher Forcing 与生成时逐步解码存在暴露差异。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 因果mask | 禁止关注未来位置 |
| 位置编码原因 | 注意力本身不编码序列顺序 |
| Encoder/Decoder差异 | Decoder多因果自注意力和交叉注意力 |

## Related Notes

- [[Self-Attention与Multi-Head Attention]]
- [[Attention与Query-Key-Value]]
- [[RNN、BPTT与序列建模]]
- [[练习-序列模型、注意力与Transformer]]
- [[34-机器学习高频易错点]]

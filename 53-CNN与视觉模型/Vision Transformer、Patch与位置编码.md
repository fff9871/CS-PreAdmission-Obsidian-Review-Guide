---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第1、8页：VIT主题；第10页Transformer与多头注意力
keywords:
- machine-learning
- computer-vision
- vision-transformer
- patch-embedding
---

# Vision Transformer、Patch与位置编码（★★★）

#machine-learning #computer-vision #vision-transformer #patch-embedding

## Overview Table

| 组件 | 作用 |
|---|---|
| Patchify | 把图像切成固定大小 patch |
| Patch Embedding | 展平/卷积投影为 token 向量 |
| Position Embedding | 注入空间顺序 |
| Transformer Encoder | 自注意力 + MLP 建模全局关系 |
| CLS Token/Pooling | 汇聚图像级表示 |

## Token数量

图像 `H×W`、patch `P×P`，token 数约为 `N=HW/P²`。Self-Attention 对 token 数的时间/显存复杂度通常为 `O(N²)`，更小 patch 提高分辨率但代价快速增加。

    image → patches → embeddings + positions
          → Transformer blocks → CLS/pool → classifier

ViT 的全局关系建模强，但原生局部和平移归纳偏置弱于 CNN，通常更依赖数据规模、预训练和增强；混合架构可结合两者。

> [!warning]
> Patch Embedding 不只是无序切块，必须保留/注入位置；ViT 不是卷积的简单替换，数据量和计算预算会改变比较结果。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| patch减半 | token约4倍，注意力矩阵约16倍 |
| 位置编码 | 区分patch空间顺序 |
| CNN vs ViT | 局部共享偏置强 vs 全局注意力灵活 |

## Related Notes

- [[Self-Attention与Multi-Head Attention]]
- [[Transformer编码器、解码器、Mask与位置编码]]
- [[卷积神经网络的局部连接、权值共享与平移性质]]
- [[练习-CNN与视觉模型]]
- [[34-机器学习高频易错点]]

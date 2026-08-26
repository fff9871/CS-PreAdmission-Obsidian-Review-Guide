---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第10页：RNN；第7页梯度问题
keywords:
- machine-learning
- sequence-models
- rnn
- bptt
---

# RNN、BPTT与序列建模（★★★）

#machine-learning #sequence-models #rnn #bptt

## Overview Table

| 项目 | 说明 |
|---|---|
| 隐状态 | 汇总截至当前步的序列信息 |
| 参数共享 | 各时间步复用同一组权重 |
| Many-to-one | 情感分类等序列到标签 |
| Many-to-many | 标注、生成、翻译等 |
| BPTT | 在展开的时间维上反向传播 |

## 递推

`h_t=φ(W_x x_t+W_h h_{t-1}+b)`

`y_t=g(W_y h_t)`

    x1 → h1 → h2 → ... → hT
          ↑     ↑          ↑
         x2    x3         xT

BPTT 将循环网络按时间展开，梯度经过重复 Jacobian 连乘，因此长序列容易消失或爆炸。截断 BPTT 只反传有限步以控制成本。

## 双向与因果

双向 RNN 同时利用前后文，适合完整序列理解；在线预测和自回归生成不能使用未来信息，应保持因果方向。

> [!warning]
> 隐状态“包含历史”不表示无损记住所有历史；长程依赖受容量和梯度限制。双向模型在离线任务有效，但会泄漏未来信息到因果任务。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| RNN参数是否随序列变长 | 不变，时间步共享参数 |
| BPTT | 在展开时间图上应用链式法则 |
| 长依赖问题 | 梯度连乘导致消失/爆炸 |

## Related Notes

- [[LSTM、GRU与门控机制]]
- [[梯度消失、梯度爆炸与参数初始化]]
- [[Self-Attention与Multi-Head Attention]]
- [[练习-序列模型、注意力与Transformer]]
- [[34-机器学习高频易错点]]

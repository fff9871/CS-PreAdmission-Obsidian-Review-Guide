---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第7、10页：LSTM与门控缓解梯度消失
keywords:
- machine-learning
- sequence-models
- lstm
- gru
---

# LSTM、GRU与门控机制（★★★）

#machine-learning #sequence-models #lstm #gru

## Overview Table

| 模型 | 核心状态/门 | 特点 |
|---|---|---|
| Vanilla RNN | 单一隐状态 | 简单，长依赖困难 |
| LSTM | cell state + 输入/遗忘/输出门 | 控制写入、保留与读出 |
| GRU | 更新门 + 重置门 | 状态更少、计算较轻 |

## LSTM直觉

    old cell c_{t-1}
       × forget gate
       + candidate × input gate
       → new cell c_t
       → tanh × output gate → h_t

cell state 的加法路径让梯度有较直接的传播通道，门控学习在不同时间尺度保存或清除信息。

## GRU直觉

GRU 把 cell 与 hidden 合并，用更新门在旧状态与候选状态之间插值；重置门控制生成候选时使用多少历史。

> [!warning]
> LSTM/GRU 是缓解而非彻底消除长程依赖问题；它们仍是时间步串行计算，难以像 Transformer 那样在序列维并行训练。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| LSTM三门 | 输入、遗忘、输出门 |
| GRU两门 | 更新、重置门 |
| 门控作用 | 自适应控制信息保留、写入和暴露 |

## Related Notes

- [[RNN、BPTT与序列建模]]
- [[Attention与Query-Key-Value]]
- [[梯度消失、梯度爆炸与参数初始化]]
- [[练习-序列模型、注意力与Transformer]]
- [[34-机器学习高频易错点]]

---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: RNN、LSTM、Attention、多头注意力与Transformer
keywords:
- practice
- machine-learning
- sequence-models
---

# 序列模型、注意力与Transformer Practice（10 questions）

#practice #machine-learning #sequence-models

## Related Concepts

- [[RNN、BPTT与序列建模]]
- [[LSTM、GRU与门控机制]]
- [[Attention与Query-Key-Value]]
- [[Self-Attention与Multi-Head Attention]]
- [[Transformer编码器、解码器、Mask与位置编码]]

> [!hint]- 核心模式（点击查看）
> | 题型 | 回答路径 |
> |---|---|
> | 定义 | 任务、假设、目标函数、输出 |
> | 比较 | 偏差、方差、计算、数据与适用场景 |

---

## Question 1 - RNN递推 [recall]
> RNN为什么能处理可变长度序列？

> [!answer]- 答案
> 它在时间步复用同一参数，并通过隐状态递归汇总历史信息。

---

## Question 2 - BPTT [recall]
> BPTT 是什么？

> [!answer]- 答案
> 把循环网络沿时间展开，在展开的计算图上反向传播梯度。

---

## Question 3 - 门控 [recall]
> LSTM 与 GRU 的门控分别有哪些？

> [!answer]- 答案
> LSTM有输入、遗忘、输出门；GRU有更新和重置门。

---

## Question 4 - QKV [recall]
> Attention中Query、Key、Value的直觉是什么？

> [!answer]- 答案
> Query表示检索需求，Key用于匹配，Value是按匹配权重汇聚的内容。

---

## Question 5 - 缩放 [recall]
> 点积注意力为什么除以√dk？

> [!answer]- 答案
> 控制高维点积方差，避免Softmax过度饱和和梯度过小。

---

## Question 6 - 位置编码 [recall]
> Transformer为何需要位置编码？

> [!answer]- 答案
> 自注意力本身缺乏token顺序信息，需要显式注入位置关系。

---

## Question 7 - Mask应用 [application]
> 自回归语言模型训练时应使用什么mask？

> [!answer]- 答案
> 使用causal mask，确保位置t只能关注自身及之前位置，并另用padding mask屏蔽填充。

---

## Question 8 - 多头维度 [application]
> d_model=512、8个头时常见每头维度是多少？

> [!answer]- 答案
> 通常是512/8=64，Q/K/V分别投影到8个64维子空间。

---

## Question 9 - RNN与Transformer [analysis]
> 两者处理长依赖的路径和并行性有何不同？

> [!answer]- 答案
> RNN信息沿时间逐步传递、路径长且串行；Self-Attention任意位置直接交互并可并行，但标准复杂度随n²增长。

---

## Question 10 - 多头边界 [analysis]
> 为什么不能简单认为注意力头越多效果越好？

> [!answer]- 答案
> 总维度固定时每头会变窄，且头可能冗余；效果受任务、数据、优化和计算预算共同限制。

---

> [!summary]- 模式总结（点击查看）
> | 维度 | 检查项 |
> |---|---|
> | 数据 | 划分、尺度、分布与泄漏 |
> | 模型 | 假设、损失、正则与优化 |
> | 评估 | 指标、阈值、方差与部署差异 |

## Related Notes

- [[32-机器学习学习地图]]
- [[34-机器学习高频易错点]]

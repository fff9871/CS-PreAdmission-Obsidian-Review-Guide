---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
- 6系2020年推免复试参考资料.pdf
part: 主资料第8、10页；6系资料第20页神经网络训练问题
keywords:
- machine-learning
- deep-learning
- mlp
- forward-propagation
---

# 感知机、MLP与前向传播（★★★）

#machine-learning #deep-learning #mlp #forward-propagation

## Overview Table

| 模型 | 计算 | 表达能力 |
|---|---|---|
| 感知机 | `sign(wᵀx+b)` | 线性可分二分类 |
| 单隐层 MLP | 线性层 + 非线性 + 线性层 | 可逼近广泛连续函数 |
| 深层网络 | 多层表示逐级组合 | 学习层次化特征 |

## 前向传播

第 l 层：

`z^[l]=W^[l]a^[l-1]+b^[l]`

`a^[l]=φ(z^[l])`

    x → Linear → Activation → ... → Logits → Loss(y)

没有非线性激活时，多层线性变换仍等价于一个线性变换。输出层与损失应匹配：多类 logits + CrossEntropy，二元 logits + BCEWithLogits，回归常用线性输出。

> [!warning]
> 万能逼近定理描述存在性，不保证有限数据、有限参数下容易训练或泛化。感知机对线性不可分数据不保证收敛。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 为什么需要激活 | 打破多层线性组合的线性等价性 |
| logits | 激活前分数，损失常内部做 Softmax/Sigmoid |
| MLP层参数 | 权重矩阵 + 偏置向量 |

## Related Notes

- [[反向传播、链式法则与计算图]]
- [[Sigmoid、Tanh、ReLU与激活函数]]
- [[PyTorch的Tensor、Autograd与计算图]]
- [[练习-神经网络训练与优化]]
- [[34-机器学习高频易错点]]

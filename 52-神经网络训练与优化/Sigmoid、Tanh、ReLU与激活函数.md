---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第12-13页：Sigmoid、ReLU与稀疏性
keywords:
- machine-learning
- deep-learning
- activation-functions
- relu
---

# Sigmoid、Tanh、ReLU与激活函数（★★★）

#machine-learning #deep-learning #activation-functions #relu

## Overview Table

| 激活 | 范围 | 优点 | 风险 |
|---|---|---|---|
| Sigmoid | `(0,1)` | 概率门控 | 饱和、非零中心、梯度小 |
| Tanh | `(-1,1)` | 零中心 | 两端饱和 |
| ReLU | `[0,∞)` | 计算简单、正区梯度稳定、稀疏激活 | dead ReLU、负区梯度0 |
| Leaky ReLU | 负区小斜率 | 缓解死亡 | 斜率是超参数 |
| GELU/SiLU | 平滑门控 | Transformer/现代网络常见 | 计算略复杂 |

## 导数与饱和

`σ'(z)=σ(z)(1-σ(z))≤0.25`

`ReLU'(z)=1(z>0)`（零点按实现约定）。深层网络中多个小导数相乘会造成梯度消失。

ReLU 的稀疏性来自负输入输出为 0，而不是让权重本身稀疏。输出层激活应按任务选择，不应机械使用 ReLU。

> [!warning]
> ReLU 只能缓解部分梯度消失，不解决梯度爆炸，也可能永久死亡；分类训练若使用 logits 版交叉熵，模型末层通常不手动加 Softmax。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| Sigmoid问题 | 饱和区梯度小、非零中心 |
| ReLU稀疏 | 负输入映射为0 |
| 多类输出 | logits + Softmax交叉熵 |

## Related Notes

- [[感知机、MLP与前向传播]]
- [[梯度消失、梯度爆炸与参数初始化]]
- [[逻辑回归、Sigmoid与交叉熵]]
- [[练习-神经网络训练与优化]]
- [[34-机器学习高频易错点]]

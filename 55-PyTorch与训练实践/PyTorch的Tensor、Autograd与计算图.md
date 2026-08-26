---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第13-14页：PyTorch训练与反向传播
keywords:
- machine-learning
- pytorch
- tensor
- autograd
---

# PyTorch的Tensor、Autograd与计算图（★★★）

#machine-learning #pytorch #tensor #autograd

## Overview Table

| 概念 | 作用 |
|---|---|
| Tensor | 带dtype、device、shape的多维数组 |
| `requires_grad` | 记录对该张量的可微操作 |
| `grad_fn` | 产生张量的反向函数节点 |
| `.backward()` | 从标量输出反向累积叶子梯度 |
| `torch.no_grad()` | 关闭梯度记录以节省内存 |
| `.detach()` | 返回与计算图分离的共享存储视图 |

## 动态计算图

    leaf parameters
       → differentiable ops
       → loss scalar
       → loss.backward()
       → parameter.grad accumulates

PyTorch 默认每次前向动态构建图，backward 后中间图通常释放。梯度默认累积，因此每次更新前需清零。

## Device与dtype

模型和输入必须位于兼容设备、通常还需兼容 dtype。混合精度用低精度前向配合梯度缩放，降低显存并提高吞吐，同时防止小梯度下溢。

> [!warning]
> `.detach()` 不复制数据，原地修改可能互相影响；`.item()`会把标量同步取回CPU，频繁调用可能造成性能同步点。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 梯度为何越来越大 | 未在每步清零，梯度累积 |
| 推理省内存 | `no_grad`/`inference_mode` + `eval()` |
| detach | 停止梯度路径，不等于深拷贝 |

## Related Notes

- [[反向传播、链式法则与计算图]]
- [[PyTorch的模型、参数与前向传播]]
- [[PyTorch训练循环、Loss与Optimizer]]
- [[练习-PyTorch与训练实践]]
- [[34-机器学习高频易错点]]

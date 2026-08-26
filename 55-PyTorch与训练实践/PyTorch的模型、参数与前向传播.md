---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第13-14页：ResNet、Conv2d、BN与Dropout模块
keywords:
- machine-learning
- pytorch
- nn-module
- model-parameters
---

# PyTorch的模型、参数与前向传播（★★★）

#machine-learning #pytorch #nn-module #model-parameters

## Overview Table

| API | 作用 |
|---|---|
| `nn.Module` | 组织子模块、参数和状态 |
| `forward` | 定义前向计算 |
| `parameters()` | 返回可训练Parameter迭代器 |
| `state_dict()` | 参数和持久缓冲的映射 |
| `to(device)` | 移动参数与缓冲 |

## 模块注册

把子层赋给 `self.xxx`，PyTorch 才会自动注册参数；普通 Python list 中的层不会自动注册，应使用 `nn.ModuleList/Sequential`。

    class Model(nn.Module)
      __init__: define layers
      forward: compose tensor operations

调用 `model(x)` 会执行 hooks 和 `forward`，通常不直接手动调用 `model.forward(x)`。

## 参数与缓冲

Parameter 参与优化；Buffer 如 BatchNorm running mean 会进入 state_dict、随设备移动，但默认不由优化器更新。

> [!warning]
> `model.eval()`不会冻结参数或关闭梯度；冻结需设置 `requires_grad=False` 并正确配置优化器。保存完整对象耦合代码，通常优先保存 state_dict。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 子层为何用ModuleList | 确保参数注册和设备/state_dict管理 |
| parameter vs buffer | 优化器更新 vs 状态随模型保存移动 |
| 冻结模型 | requires_grad + optimizer参数选择 |

## Related Notes

- [[PyTorch的Tensor、Autograd与计算图]]
- [[PyTorch的Conv2d、MaxPool2d与形状推导]]
- [[ResNet、残差块与迁移学习]]
- [[练习-PyTorch与训练实践]]
- [[34-机器学习高频易错点]]

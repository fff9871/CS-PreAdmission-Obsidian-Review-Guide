---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第13页：训练ResNet代码示例
keywords:
- machine-learning
- pytorch
- training-loop
- optimizer
---

# PyTorch训练循环、Loss与Optimizer（★★★）

#machine-learning #pytorch #training-loop #optimizer

## Overview Table

| 步骤 | 典型调用 |
|---|---|
| 训练模式 | `model.train()` |
| 清梯度 | `optimizer.zero_grad()` |
| 前向 | `logits=model(x)` |
| 损失 | `loss=criterion(logits,y)` |
| 反向 | `loss.backward()` |
| 更新 | `optimizer.step()` |

## 标准循环

    for batch in loader:
      move data → zero_grad → forward
      → compute loss → backward
      → optional clip/scale → optimizer.step
      → scheduler step at defined frequency

`CrossEntropyLoss` 期望未Softmax的 logits 和整数类别索引；二分类可用 `BCEWithLogitsLoss`。记录 epoch loss 应按样本数/批量大小正确加权，而不是只累计最后一个 batch。

## 梯度累积

显存不足时可把 loss 除以累积步数，连续 backward 后再 step，模拟更大有效 batch；需同步调整 scheduler 和 BN 语义。

> [!warning]
> 清梯度、反向、更新顺序不能颠倒；`running_loss` 每个 epoch 清零，而 `optimizer` 应在训练循环外创建，否则动量状态会丢失。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| CrossEntropy输入 | logits + Long类别索引 |
| zero_grad原因 | PyTorch梯度默认累积 |
| 梯度裁剪时机 | backward之后、step之前 |

## Related Notes

- [[PyTorch的Tensor、Autograd与计算图]]
- [[Dataset、DataLoader、Batch与Shuffle]]
- [[Adagrad、RMSprop与Adam]]
- [[练习-PyTorch与训练实践]]
- [[34-机器学习高频易错点]]

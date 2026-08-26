---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第14页：BN与Dropout训练测试差异
keywords:
- machine-learning
- pytorch
- train-eval-mode
- batch-normalization
---

# PyTorch的train-eval、BatchNorm与Dropout（★★★）

#machine-learning #pytorch #train-eval-mode #batch-normalization

## Overview Table

| 模式 | BatchNorm | Dropout | 梯度记录 |
|---|---|---|---|
| `model.train()` | batch统计、更新running stats | 随机丢弃 | 默认仍开启 |
| `model.eval()` | running统计 | 关闭 | 默认仍开启 |
| `no_grad()` | 不改变模块模式 | 不改变模块模式 | 关闭记录 |

## 验证模板

    model.eval()
    with torch.no_grad():
        for x,y in val_loader:
            logits=model(x)
            accumulate metrics

验证结束后进入下一训练阶段需重新 `model.train()`。Monte Carlo Dropout 等特殊方法会有意在推理时保持 Dropout，但必须明确目的。

## BatchNorm状态

`weight/bias` 是可学习参数；`running_mean/variance` 是缓冲。冻结参数不自动冻结 running 统计，需结合模块模式控制。

> [!warning]
> `eval()`与`no_grad()`必须区分：前者控制层行为，后者控制自动求导；只使用其中一个都可能得到错误结果或浪费内存。

## Exam/Test Patterns

| 场景 | 调用 |
|---|---|
| 普通训练 | train + grad enabled |
| 普通验证 | eval + no_grad |
| 冻结权重 | requires_grad=False，另处理BN模式 |

## Related Notes

- [[归一化：BatchNorm、LayerNorm、GroupNorm与InstanceNorm]]
- [[Dropout、早停与数据增强]]
- [[PyTorch训练循环、Loss与Optimizer]]
- [[练习-PyTorch与训练实践]]
- [[34-机器学习高频易错点]]

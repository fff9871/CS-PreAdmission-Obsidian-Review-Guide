---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: Tensor、Module、Conv2d、DataLoader、训练循环、模式与调试
keywords:
- practice
- machine-learning
- pytorch
---

# PyTorch与训练实践 Practice（10 questions）

#practice #machine-learning #pytorch

## Related Concepts

- [[PyTorch的Tensor、Autograd与计算图]]
- [[PyTorch的模型、参数与前向传播]]
- [[PyTorch的Conv2d、MaxPool2d与形状推导]]
- [[Dataset、DataLoader、Batch与Shuffle]]
- [[PyTorch训练循环、Loss与Optimizer]]
- [[PyTorch的train-eval、BatchNorm与Dropout]]
- [[Loss与Accuracy曲线诊断]]
- [[检查点、迁移学习与可复现训练]]

> [!hint]- 核心模式（点击查看）
> | 题型 | 回答路径 |
> |---|---|
> | 定义 | 任务、假设、目标函数、输出 |
> | 比较 | 偏差、方差、计算、数据与适用场景 |

---

## Question 1 - 梯度累积 [recall]
> 为什么训练循环每步通常要zero_grad？

> [!answer]- 答案
> PyTorch默认把新梯度累加到参数.grad，不清零会跨batch累积。

---

## Question 2 - Module [recall]
> 为什么子层应赋给self属性或放入ModuleList？

> [!answer]- 答案
> 这样PyTorch才能注册参数，并正确处理state_dict、设备移动和train/eval。

---

## Question 3 - Conv形状 [recall]
> Conv2d权重张量的形状是什么？

> [!answer]- 答案
> [out_channels, in_channels/groups, kernel_h, kernel_w]。

---

## Question 4 - DataLoader [recall]
> Dataset与DataLoader分别负责什么？

> [!answer]- 答案
> Dataset定义样本访问，DataLoader负责采样、批处理、多进程加载和拼接。

---

## Question 5 - 训练顺序 [recall]
> 标准训练步的调用顺序是什么？

> [!answer]- 答案
> zero_grad→forward→loss→backward→optimizer.step。

---

## Question 6 - 评估模式 [recall]
> 标准验证为什么同时需要eval和no_grad？

> [!answer]- 答案
> eval切换BN/Dropout行为，no_grad关闭梯度记录；两者职责不同。

---

## Question 7 - 损失输入 [application]
> 多分类模型用CrossEntropyLoss时，前向应输出Softmax概率还是logits？

> [!answer]- 答案
> 输出未Softmax的logits，CrossEntropyLoss内部稳定地完成log-softmax。

---

## Question 8 - 断点续训 [application]
> 要完整恢复Adam混合精度训练，应保存哪些状态？

> [!answer]- 答案
> 模型、优化器、scheduler、GradScaler、epoch/step、配置，严格恢复时再保存RNG状态。

---

## Question 9 - 曲线冲突 [analysis]
> 为什么accuracy上升时loss仍可能上升？

> [!answer]- 答案
> 更多样本跨过分类阈值会提升accuracy，但少数错误若变得极高置信，会显著增大交叉熵。

---

## Question 10 - 冻结边界 [analysis]
> 为什么requires_grad=False仍不足以完全冻结含BN的backbone行为？

> [!answer]- 答案
> 它只阻止参数梯度，BN在train模式仍会更新running统计，需同时控制模块模式或单独冻结BN。

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

---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
- 计算机保研英语名词.pdf
part: 卷积形状、池化、感受野、可分离卷积、ResNet与ViT
keywords:
- practice
- machine-learning
- computer-vision
---

# CNN与视觉模型 Practice（10 questions）

#practice #machine-learning #computer-vision

## Related Concepts

- [[卷积运算、通道、步幅与填充]]
- [[卷积输出尺寸、参数量与计算量]]
- [[池化、全局平均池化与下采样]]
- [[感受野与空洞卷积]]
- [[1x1卷积与深度可分离卷积]]
- [[卷积神经网络的局部连接、权值共享与平移性质]]
- [[ResNet、残差块与迁移学习]]
- [[Vision Transformer、Patch与位置编码]]

> [!hint]- 核心模式（点击查看）
> | 题型 | 回答路径 |
> |---|---|
> | 定义 | 任务、假设、目标函数、输出 |
> | 比较 | 偏差、方差、计算、数据与适用场景 |

---

## Question 1 - 卷积通道 [recall]
> 普通Conv2d单个输出通道的卷积核跨多少输入通道？

> [!answer]- 答案
> 跨全部Cin/groups个输入通道，对各通道卷积结果求和。

---

## Question 2 - 输出尺寸 [recall]
> 卷积输出空间尺寸由哪些参数决定？

> [!answer]- 答案
> 输入尺寸、padding、kernel、dilation和stride。

---

## Question 3 - GAP [recall]
> 全局平均池化把NCHW变成什么形状？

> [!answer]- 答案
> 对每通道H×W求均值，得到N×C。

---

## Question 4 - 空洞卷积 [recall]
> 3×3核、dilation=2的有效核大小是多少？

> [!answer]- 答案
> 有效大小为2×(3-1)+1=5，即覆盖5×5范围。

---

## Question 5 - 可分离卷积 [recall]
> 深度可分离卷积的两个步骤是什么？

> [!answer]- 答案
> 逐通道空间卷积，再用1×1逐点卷积混合通道。

---

## Question 6 - CNN偏置 [recall]
> CNN参数较少的两个主要原因是什么？

> [!answer]- 答案
> 局部连接和跨空间位置的权值共享。

---

## Question 7 - 形状应用 [application]
> 输入32×32，3×3卷积、padding=1、stride=2、dilation=1，输出边长是多少？

> [!answer]- 答案
> floor((32+2-2-1)/2)+1=16。

---

## Question 8 - ViT计算 [application]
> patch边长从16减为8，图像不变时token和注意力矩阵规模如何变化？

> [!answer]- 答案
> token数约增至4倍，自注意力N²矩阵约增至16倍。

---

## Question 9 - 参数延迟 [analysis]
> 为什么深度可分离卷积参数更少却不一定在所有硬件上更快？

> [!answer]- 答案
> 真实速度还受内存访问、并行度、算子融合和内核实现影响，理论FLOPs不是唯一瓶颈。

---

## Question 10 - CNN与ViT [analysis]
> CNN和ViT在归纳偏置上如何取舍？

> [!answer]- 答案
> CNN内置局部连接和平移共享，数据效率高；ViT用全局注意力更灵活，但常更依赖预训练、数据和计算。

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

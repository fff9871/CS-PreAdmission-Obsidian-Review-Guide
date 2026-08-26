---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第13-14页：Conv2d与MaxPooling参数
keywords:
- machine-learning
- pytorch
- conv2d
- maxpool2d
---

# PyTorch的Conv2d、MaxPool2d与形状推导（★★★）

#machine-learning #pytorch #conv2d #maxpool2d

## Overview Table

| 模块 | 关键参数 |
|---|---|
| `nn.Conv2d` | in/out channels、kernel、stride、padding、dilation、groups、bias |
| `nn.MaxPool2d` | kernel、stride、padding、dilation、ceil_mode |
| `nn.AdaptiveAvgPool2d` | 直接指定输出空间大小 |

## 形状检查

PyTorch图像张量默认 NCHW。卷积权重形状是 `[Cout,Cin/groups,Kh,Kw]`。输出空间使用标准卷积公式；MaxPool 默认 stride 等于 kernel size（若未显式给出）。

    [N,3,224,224]
      → Conv2d(3,64,7,stride=2,padding=3)
      → [N,64,112,112]
      → MaxPool2d(3,stride=2,padding=1)
      → [N,64,56,56]

可用最小 dummy tensor 在构造阶段或测试中验证形状，但正式代码仍应理解公式和动态尺寸。

> [!warning]
> `padding='same'`、ceil_mode和偶数核会影响精确结果；flatten时不要硬编码错误空间尺寸，可用Adaptive Pool或Lazy层。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| Conv2d第二参数 | 输出通道数/卷积核组数 |
| groups=Cin | Depthwise卷积条件之一 |
| 自适应池化 | 不依输入尺寸固定输出H×W |

## Related Notes

- [[卷积运算、通道、步幅与填充]]
- [[卷积输出尺寸、参数量与计算量]]
- [[PyTorch的模型、参数与前向传播]]
- [[练习-PyTorch与训练实践]]
- [[34-机器学习高频易错点]]

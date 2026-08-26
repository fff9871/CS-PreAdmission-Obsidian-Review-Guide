---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第4页：SVM、支持向量与最大间隔
keywords:
- machine-learning
- supervised-learning
- svm
- maximum-margin
---

# 线性SVM、间隔与支持向量（★★★）

#machine-learning #supervised-learning #svm #maximum-margin

## Overview Table

| 概念 | 含义 |
|---|---|
| 超平面 | `wᵀx+b=0` |
| 几何间隔 | 样本到超平面的距离 |
| 支持向量 | 位于间隔边界或违反间隔的关键样本 |
| Hinge loss | `max(0,1-yf(x))` |

## 软间隔目标

`min 1/2||w||² + CΣξ_i`

约束 `y_i(wᵀx_i+b) ≥ 1-ξ_i, ξ_i≥0`。

`||w||` 越小，几何间隔越大；C 控制间隔最大化与训练违例惩罚的权衡。

    class + :      +  + | margin | +
    hyperplane: -------- wᵀx+b=0
    class - :   - | margin | -  -

只有支持向量决定最终边界，远离间隔的样本对解通常无直接影响。

> [!warning]
> SVM 最大化的是规范化几何间隔，不是任意缩放下的函数间隔。C 大表示更重视训练违例，不等于正则更强。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 支持向量 | 靠近/进入间隔、决定边界的样本 |
| C 增大 | 对误分惩罚更强，边界可能更复杂 |
| 线性不可分 | 软间隔或核方法 |

## Related Notes

- [[核技巧、软间隔与多分类SVM]]
- [[L1、L2正则化与稀疏性]]
- [[逻辑回归、Sigmoid与交叉熵]]
- [[练习-经典监督学习与集成]]
- [[34-机器学习高频易错点]]

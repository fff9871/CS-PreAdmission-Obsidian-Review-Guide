---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第4页：核技巧、SVM优缺点与多分类
keywords:
- machine-learning
- supervised-learning
- kernel-methods
- multiclass-svm
---

# 核技巧、软间隔与多分类SVM（★★★）

#machine-learning #supervised-learning #svm #kernel-methods

## Overview Table

| 核 | 形式/特点 |
|---|---|
| Linear | `xᵀz`，高维稀疏常有效 |
| Polynomial | `(γxᵀz+r)^d` |
| RBF | `exp(-γ||x-z||²)`，局部相似性 |
| Sigmoid | 类神经元形式，并非所有参数都满足有效核条件 |

## 核技巧

核函数直接计算特征映射后的内积 `K(x,z)=φ(x)ᵀφ(z)`，无需显式构造高维 `φ(x)`。有效核需使任意样本上的 Gram 矩阵半正定。

## 超参数与多分类

- RBF 中 γ 大：影响范围窄，边界更复杂；γ 小：更平滑。
- C 控制违例惩罚。
- 多分类常用 One-vs-Rest 或 One-vs-One。

核 SVM 训练和预测成本随样本/支持向量增加，大规模数据常改用线性 SVM、近似核或其他模型。

> [!warning]
> 核技巧不是“先真的映射再计算”，价值恰在隐式内积；SVM 可做多分类，只是需分解或专门多类目标。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| RBF γ 大 | 局部、复杂、高方差风险 |
| One-vs-One | K 类需 K(K-1)/2 个分类器 |
| 核矩阵条件 | 对称半正定 |

## Related Notes

- [[线性SVM、间隔与支持向量]]
- [[KNN、距离度量与K值选择]]
- [[PCA、SVD与降维方法选择]]
- [[练习-经典监督学习与集成]]
- [[34-机器学习高频易错点]]

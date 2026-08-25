---
source_pdf:
  - "【精品】计算机保研面试_数学常见题.pdf"
  - "CUMT保研数学类复习指南(秋月版).pdf"
  - "【精品】计算机保研面试专业课常见问题.pdf"
part: "数学题集第6页；CUMT 第31页；专业课题集第46页"
keywords: [singular-value-decomposition, pca, low-rank-approximation, pseudoinverse]
---

# 奇异值分解与 PCA（★★★）

#linear-algebra #matrix-decomposition #svd

## Overview Table

| 对象 | 关系 |
|---|---|
| SVD | $A=U\Sigma V^T$ |
| 右奇异向量 | $A^TA$ 的标准正交特征向量 |
| 左奇异向量 | $AA^T$ 的标准正交特征向量 |
| 奇异值 | $\sigma_i=\sqrt{\lambda_i(A^TA)}$ |

## SVD 的几何过程

对任意 $m\times n$ 实矩阵：

```text
x ──Vᵀ──> 旋转/反射到右奇异坐标
  ──Σ───> 沿坐标轴缩放并改变维度
  ──U───> 旋转/反射到输出空间
```

SVD 不要求方阵，也不要求矩阵可对角化。

## 低秩近似

若奇异值按 $\sigma_1\ge\cdots\ge\sigma_r>0$ 排序，则

$$A=\sum_{i=1}^r\sigma_i u_iv_i^T.$$

截断到前 $k$ 项得到最佳秩 $k$ 近似（对 2-范数和 Frobenius 范数）：

$$A_k=\sum_{i=1}^k\sigma_i u_iv_i^T.$$

## 伪逆

$$A^+=V\Sigma^+U^T,$$

其中非零奇异值取倒数。它统一给出最小二乘与最小范数解。

## PCA 联系

将样本中心化为矩阵 $X$：

- 协方差矩阵特征向量给出主方向；
- 直接对 $X$ 做 SVD，可避免显式形成协方差矩阵；
- 保留最大奇异值对应方向完成降维。

> [!warning]
> PCA 通常先中心化；是否标准化取决于特征量纲。奇异值不是 $A^TA$ 的特征值，而是其平方根。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| “SVD 适用范围” | 任意矩阵 |
| “奇异值怎么求” | $A^TA$ 非负特征值的平方根 |
| “低秩近似” | 保留最大的若干奇异值及奇异向量 |
| “PCA 与 SVD” | 中心化数据的主成分可由 SVD 直接获得 |

## Related Notes

- [[实对称矩阵与谱分解]]
- [[向量范数与矩阵范数]]
- [[超定、欠定系统与最小二乘]]
- [[矩阵与张量]]
- [[练习-特征值与分解]]
- [[10-线性代数高频易错点]]


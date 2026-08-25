---
source_pdf:
  - "CUMT保研数学类复习指南(秋月版).pdf"
  - "线性代数.pdf"
part: "CUMT 第27、31页；线代第6、14页"
keywords: [lu-decomposition, qr-decomposition, matrix-factorization, numerical-linear-algebra]
---

# LU、QR 与常用矩阵分解（★★）

#linear-algebra #matrix-decomposition

## Overview Table

| 分解 | 形式 | 主要用途 |
|---|---|---|
| LU | $PA=LU$ | 解方程、行列式、重复右端项 |
| QR | $A=QR$ | 最小二乘、正交化 |
| Cholesky | $A=LL^T$ | 对称正定系统 |
| EVD | $A=PDP^{-1}$ | 可对角化方阵 |
| SVD | $A=U\Sigma V^T$ | 任意矩阵、低秩近似 |

## LU 分解

高斯消元把矩阵写成下三角与上三角矩阵乘积。带主元交换时写作 $PA=LU$。

```text
Ax=b
PA=LU
 ↓
先解 Ly=Pb
再解 Ux=y
```

若多次求解相同 $A$、不同 $b$，只需分解一次。

## QR 分解

$A=QR$，其中 $Q$ 列正交、$R$ 上三角。QR 可由 Gram-Schmidt、Householder 或 Givens 旋转构造。

最小二乘中：

$$\min\|Ax-b\|_2=\min\|Rx-Q^Tb\|_2.$$

## Cholesky 分解

实对称正定矩阵存在唯一的正对角 Cholesky 分解 $A=LL^T$，计算量约为一般 LU 的一半。

## 分解选择

| 问题 | 优先选择 |
|---|---|
| 一般方阵线性系统 | 带主元 LU |
| 最小二乘 | QR |
| 对称正定系统 | Cholesky |
| 秩亏/低秩/伪逆 | SVD |

> [!warning]
> 理论上能写正规方程，不代表数值上最优；QR/SVD 通常比直接形成 $A^TA$ 更稳定。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| “LU 用途” | 把消元复用为两次三角系统求解 |
| “QR 用途” | 构造正交基、稳定求最小二乘 |
| “Cholesky 条件” | 实对称正定 |
| “任意矩阵分解” | SVD 最通用 |

## Related Notes

- [[逆矩阵、伴随矩阵与初等变换]]
- [[内积、正交与Gram-Schmidt正交化]]
- [[超定、欠定系统与最小二乘]]
- [[奇异值分解与PCA]]
- [[练习-特征值与分解]]
- [[10-线性代数高频易错点]]


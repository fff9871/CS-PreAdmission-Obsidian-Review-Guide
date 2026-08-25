---
source_pdf:
  - "线性代数.pdf"
  - "【精品】计算机保研面试_数学常见题.pdf"
  - "【精品】计算机保研面试专业课常见问题.pdf"
  - "6系2020年推免复试参考资料.pdf"
part: "线代第3、16页；数学题集第4-5页；专业课题集第44页；6系第14页"
keywords: [inner-product, orthogonality, gram-schmidt, orthonormal-basis]
---

# 内积、正交与 Gram-Schmidt 正交化（★★★）

#linear-algebra #inner-product #orthogonality

## Overview Table

| 概念 | 条件 |
|---|---|
| 内积 | 正定、共轭对称、线性 |
| 正交 | $\langle u,v\rangle=0$ |
| 标准正交 | 两两正交且每个范数为 1 |
| 投影 | $\operatorname{proj}_u v=\frac{\langle v,u\rangle}{\langle u,u\rangle}u$ |

## 内积与几何量

欧氏空间中 $\langle x,y\rangle=x^Ty$，并定义

$$\|x\|_2=\sqrt{\langle x,x\rangle},\qquad
\cos\theta=\frac{\langle x,y\rangle}{\|x\|\|y\|}.$$

正交非零向量必线性无关。

## Gram-Schmidt

给定线性无关组 $v_1,ldots,v_k$：

$$u_1=v_1,$$
$$u_j=v_j-\sum_{i<j}\frac{\langle v_j,u_i\rangle}{\langle u_i,u_i\rangle}u_i,$$
$$q_j=u_j/\|u_j\|.$$

```text
原向量 vj
 - 在已有正交方向上的全部投影
 = 新的正交分量 uj
 → 单位化得到 qj
```

## 函数空间内积

连续函数可定义加权内积

$$\langle f,g\rangle=\int_a^b f(x)\overline{g(x)}w(x)\,dx,$$

说明“向量”与“正交”不限于有限维坐标列。

> [!warning]
> 原始 Gram-Schmidt 在数值计算中可能不稳定；实际常用修正 Gram-Schmidt 或 Householder QR。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| “正交与标准正交” | 后者还要求单位长度 |
| “正交化步骤” | 依次减去在已有正交方向上的投影，再单位化 |
| “正交为何无关” | 与线性组合取内积可逐个推出系数为零 |
| “内积作用” | 定义长度、夹角、正交和投影 |

## Related Notes

- [[正交矩阵与正交投影]]
- [[向量范数与矩阵范数]]
- [[LU、QR与常用矩阵分解]]
- [[练习-正交与范数]]
- [[10-线性代数高频易错点]]


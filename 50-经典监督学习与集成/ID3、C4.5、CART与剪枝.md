---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第3页：ID3、C4.5、预剪枝与后剪枝
keywords:
- machine-learning
- supervised-learning
- tree-algorithms
- pruning
---

# ID3、C4.5、CART与剪枝（★★★）

#machine-learning #supervised-learning #decision-tree #tree-algorithms #pruning

## Overview Table

| 算法 | 任务/树型 | 划分 |
|---|---|---|
| ID3 | 经典分类，多叉 | 信息增益 |
| C4.5 | 分类，多叉/连续处理 | 增益率 |
| CART | 分类与回归，二叉 | Gini / 平方误差 |

## 剪枝

| 方法 | 时机 | 特点 |
|---|---|---|
| 预剪枝 | 生长前判断是否继续 | 训练快，可能过早停止 |
| 后剪枝 | 先长大树再删子树 | 通常更稳健，计算较多 |
| 代价复杂度剪枝 | `error + α×leaves` | 用验证/CV选择 α |

树对训练数据的小变化可能产生不同结构，属于高方差模型；限制深度、叶样本数和集成可改善泛化。

## 缺失与类别特征

不同实现可用替代分裂、缺失方向、显式缺失类别或预处理。树能处理非线性，但“无需任何预处理”并不绝对。

> [!warning]
> 预剪枝和后剪枝都应依据验证性能或复杂度准则，而非只看训练误差；决策树可用于回归，不能仅定义为分类器。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| CART 是否多叉 | 标准 CART 为二叉树 |
| 防过拟合 | 深度/样本限制、预剪枝、后剪枝 |
| 树的主要统计问题 | 高方差、不稳定 |

## Related Notes

- [[决策树、信息熵与信息增益]]
- [[Bagging、随机森林与Boosting]]
- [[过拟合、欠拟合与偏差-方差]]
- [[练习-经典监督学习与集成]]
- [[34-机器学习高频易错点]]

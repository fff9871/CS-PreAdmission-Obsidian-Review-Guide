---
source_pdf:
- 计算机考研复试面试常问问题 计算机组成原理篇.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
- 专业课程基础概念复习.pdf
- 计算考研复试面试常问问题 操作系统篇.pdf
- 6系2020年推免复试参考资料.pdf
part: 存储层次、半导体存储器、主存、Cache与虚拟存储
keywords:
- practice
- computer-organization
- memory-hierarchy
- cache
---

# 存储系统与Cache Practice（10 questions）

#practice #computer-organization #memory-hierarchy #cache

## Related Concepts

- [[存储层次与局部性]]
- [[SRAM、DRAM与ROM]]
- [[主存编址、扩展与多模块交叉]]
- [[Cache结构、命中率与平均访问时间]]
- [[Cache映射方式]]
- [[Cache替换算法与写策略]]
- [[虚拟存储、页表与TLB]]

> [!hint]- 核心模式（点击查看）
> | 关键词 | 回答路径 |
> |---|---|
> | 地址划分 | block offset→set index→tag |
> | AMAT | hit time + miss rate × miss penalty |
> | 虚存 | TLB→页表→缺页处理 |

---

## Question 1 - 局部性 [recall]
> 时间局部性和空间局部性分别是什么？

> [!answer]- 答案
> 时间局部性是近期访问对象可能再次访问；空间局部性是邻近地址可能很快被访问。

---

## Question 2 - SRAM与DRAM [recall]
> Cache 和主存通常分别采用什么存储器？

> [!answer]- 答案
> Cache 常用 SRAM，主存常用 DRAM。

---

## Question 3 - 地址线 [recall]
> n 根地址线最多能选择多少个地址单元？

> [!answer]- 答案
> 最多 `2^n` 个地址单元。

---

## Question 4 - AMAT [recall]
> 写出单级 Cache 的平均访存时间公式。

> [!answer]- 答案
> `AMAT = 命中时间 + 缺失率 × 缺失代价`。

---

## Question 5 - 映射方式 [recall]
> Cache 三种基本映射方式是什么？

> [!answer]- 答案
> 直接映射、全相联映射和组相联映射。

---

## Question 6 - TLB [recall]
> TLB 缓存的是什么？

> [!answer]- 答案
> 缓存近期虚页号到物理页框号等页表项。

---

## Question 7 - 地址划分 [application]
> Cache 块大小 64 B，需要多少位块内偏移？

> [!answer]- 答案
> `log2(64)=6` 位。

---

## Question 8 - 写策略 [application]
> 写回 Cache 替换一条脏行时需要做什么？

> [!answer]- 答案
> 先把脏块写回下层存储，再装入新块。

---

## Question 9 - 相联度取舍 [analysis]
> 为什么不把所有 Cache 都设计成全相联？

> [!answer]- 答案
> 全相联减少冲突缺失，但需要大量并行 Tag 比较，增加命中延迟、面积和功耗。

---

## Question 10 - TLB与缺页 [analysis]
> TLB 未命中为什么不等于缺页？

> [!answer]- 答案
> TLB 只是页表项缓存；未命中后页表可能仍表明页面已在主存，查表并回填即可。

---

> [!summary]- 模式总结（点击查看）
> | 类型 | 判断重点 |
> |---|---|
> | 结构题 | 速度、容量、成本与局部性 |
> | 计算题 | 地址位数、组数、命中率与代价 |
> | 异常题 | 区分 TLB miss、Cache miss 和 page fault |

## Related Notes

- [[24-计算机组成学习地图]]
- [[26-计算机组成高频易错点]]

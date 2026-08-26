---
source_pdf:
- 计算机考研复试面试常问问题 计算机组成原理篇.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
- 专业课程基础概念复习.pdf
- 6系2020年推免复试参考资料.pdf
- MIPS-C指令集_校对完成版_-指令排序.pdf
- MIPS_Vol2_指令集_.pdf
- IDT R30xx Family Software Reference Manual.pdf
part: 指令格式、寻址、RISC/CISC、CPU数据通路、控制器与MIPS
keywords:
- practice
- computer-organization
- instruction-set
- cpu
---

# 指令系统与CPU Practice（10 questions）

#practice #computer-organization #instruction-set #cpu

## Related Concepts

- [[指令格式、操作码与地址码]]
- [[寻址方式与有效地址计算]]
- [[CISC与RISC]]
- [[CPU组成、寄存器与数据通路]]
- [[指令周期、机器周期与时钟周期]]
- [[控制器、硬布线与微程序控制]]
- [[MIPS-C指令分类与RISC实例]]

> [!hint]- 核心模式（点击查看）
> | 关键词 | 回答路径 |
> |---|---|
> | ISA | 格式、操作数、寄存器、寻址与可见行为 |
> | 数据通路 | PC/寄存器→ALU→存储器→写回 |
> | 控制 | 硬布线速度 vs 微程序灵活 |

---

## Question 1 - 操作码 [recall]
> 指令中的操作码字段用于什么？

> [!answer]- 答案
> 指定指令要执行的操作，必要时与功能码共同完成译码。

---

## Question 2 - 寻址方式 [recall]
> PC 相对寻址常用于哪类指令？

> [!answer]- 答案
> 常用于条件分支和位置无关控制转移。

---

## Question 3 - RISC [recall]
> RISC 的典型设计倾向有哪些？

> [!answer]- 答案
> 定长规则指令、Load/Store、大量寄存器、较少寻址方式并利于流水线。

---

## Question 4 - CPU寄存器 [recall]
> PC、IR、MAR、MDR 分别保存什么？

> [!answer]- 答案
> 下一指令地址、当前指令、主存地址和主存读写数据。

---

## Question 5 - 指令周期 [recall]
> 典型指令执行可分为哪些阶段？

> [!answer]- 答案
> 取指、译码、执行、可选访存、写回，并在边界检查中断。

---

## Question 6 - 控制器 [recall]
> 硬布线与微程序控制的主要取舍是什么？

> [!answer]- 答案
> 硬布线快但修改困难；微程序规整灵活但通常多一层控制存储访问。

---

## Question 7 - 有效地址 [application]
> 基址寄存器为 1000，位移为 24，有效地址是多少？

> [!answer]- 答案
> 按基址加位移计算，EA=1024；之后还可能进行虚拟地址翻译。

---

## Question 8 - MIPS访存 [application]
> MIPS 中 `lw $t0, 8($s0)` 的基本含义是什么？

> [!answer]- 答案
> 用 `$s0+8` 形成有效地址，从内存加载一个字到 `$t0`。

---

## Question 9 - ISA与实现 [analysis]
> 为什么同一 ISA 可以有性能差异很大的处理器？

> [!answer]- 答案
> ISA 只规定程序可见行为；流水深度、执行宽度、Cache、预测和频率等微体系结构可以不同。

---

## Question 10 - RISC与CISC [analysis]
> 为什么不能只凭 RISC/CISC 标签判断谁更快？

> [!answer]- 答案
> 两者指令数、CPI、主频、译码方式和编译器不同，现代实现还会融合多种思想，应比较完整工作负载。

---

> [!summary]- 模式总结（点击查看）
> | 类型 | 判断重点 |
> |---|---|
> | 格式题 | 位字段与操作数来源 |
> | 流程题 | 取指、译码、执行、访存、写回 |
> | 比较题 | ISA 抽象与微体系结构实现分离 |

## Related Notes

- [[24-计算机组成学习地图]]
- [[26-计算机组成高频易错点]]

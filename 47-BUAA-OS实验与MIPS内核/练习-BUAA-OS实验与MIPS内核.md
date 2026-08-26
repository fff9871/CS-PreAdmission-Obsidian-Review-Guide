---
source_pdf:
- 指导书.pdf
- OS预习指导.pdf
- 预习指导（补充）.pdf
- Lab0实验报告.pdf
- Lab1实验报告.pdf
- Lab2实验报告.pdf
- Lab3实验报告.pdf
- Lab4实验报告.pdf
- Lab5实验报告.pdf
- Lab6实验报告.pdf
part: 构建、ELF、内存、异常调度、系统调用、COW、文件系统与Shell
keywords:
- practice
- operating-systems
- buaa-mos
---

# BUAA-OS实验与MIPS内核 Practice（10 questions）

#practice #operating-systems #buaa-mos

## Related Concepts

- [[BUAA-MOS实验环境、构建与GXemul]]
- [[BUAA-MOS启动、ELF与链接脚本]]
- [[BUAA-MOS物理内存、页表与TLB重填]]
- [[BUAA-MOS进程、异常与调度]]
- [[BUAA-MOS系统调用、IPC与fork]]
- [[BUAA-MOS文件系统、管道与Shell]]

> [!hint]- 核心模式（点击查看）
> | 题型 | 回答路径 |
> |---|---|
> | 定义 | 对象、状态、机制、边界 |
> | 比较 | 目标、实现、开销、适用场景 |

---

## Question 1 - 构建链 [recall]
> 从 C/汇编源文件到 GXemul 运行内核的基本链路是什么？

> [!answer]- 答案
> 预处理/编译/汇编生成目标文件，链接脚本链接为 MIPS ELF，再由 GXemul 装载并跳转入口。

---

## Question 2 - ELF视图 [recall]
> ELF Program Header 与 Section Header 的用途有何不同？

> [!answer]- 答案
> Program Header 面向装载运行，Section Header 面向链接、重定位和调试。

---

## Question 3 - 页表映射 [recall]
> 替换已有虚拟页映射时必须同步处理哪些状态？

> [!answer]- 答案
> 旧页引用计数、新 PTE 权限与页框，以及对应 TLB 项的失效/更新。

---

## Question 4 - Trapframe [recall]
> Trapframe 在异常处理中的作用是什么？

> [!answer]- 答案
> 保存被中断执行流的寄存器与状态，供内核分派和最终恢复。

---

## Question 5 - COW [recall]
> 写时复制 fork 如何避免立即复制全部地址空间？

> [!answer]- 答案
> 父子先共享标记为 COW 的只读物理页，只有首次写入者发生异常并复制该页。

---

## Question 6 - 管道EOF [recall]
> MOS Shell 管道何时应向读者返回 EOF？

> [!answer]- 答案
> 缓冲区已读空且系统中所有写端引用都已关闭时。

---

## Question 7 - 调试启动 [application]
> 内核构建成功但跳转后立即异常，优先检查什么？

> [!answer]- 答案
> 用 readelf/objdump 核对 ELF 入口、段地址和链接符号，再检查启动栈、BSS 清零及异常现场。

---

## Question 8 - 用户指针 [application]
> 系统调用收到用户缓冲区地址后为什么不能直接信任？

> [!answer]- 答案
> 必须验证地址范围、映射和访问权限，并处理检查/使用间状态变化，避免破坏内核或越权。

---

## Question 9 - 递归异常 [analysis]
> 用户级页异常处理为何需要专用异常栈和递归布局规则？

> [!answer]- 答案
> 普通用户栈可能就是故障对象；handler 内再次异常时还需在现有异常帧下安全保存新现场，避免覆盖。

---

## Question 10 - 文件管道联动 [analysis]
> Shell 构造 A|B 时为何父子进程都必须关闭无关管道端点？

> [!answer]- 答案
> 额外写端引用会阻止 EOF，额外读写端还会泄漏资源并使阻塞关系与生命周期判断失真。

---

> [!summary]- 模式总结（点击查看）
> | 维度 | 检查项 |
> |---|---|
> | 正确性 | 明确状态、原子性与异常路径 |
> | 性能 | 说明时间、空间、并发和 I/O 开销 |

## Related Notes

- [[28-操作系统学习地图]]
- [[30-操作系统高频易错点]]

---
source_pdf:
- 操作系统_第5章_IO_wty_2021.pdf
- 操作系统_第6章_磁盘管理_wty_2021.pdf
- 操作系统_第7章_文件系统_wty_2021.pdf
- 计算考研复试面试常问问题 操作系统篇.pdf
- 指导书.pdf
part: I/O栈、异步模型、缓冲、磁盘、RAID、文件和一致性
keywords:
- practice
- operating-systems
- file-system
---

# 文件系统、磁盘与I-O Practice（10 questions）

#practice #operating-systems #file-system

## Related Concepts

- [[I-O软件层次、驱动与设备控制器]]
- [[阻塞非阻塞、同步异步与I-O多路复用]]
- [[缓冲、缓存、假脱机与设备分配]]
- [[磁盘结构、寻道与格式化]]
- [[FCFS、SSTF、SCAN与C-SCAN磁盘调度]]
- [[RAID级别、容量与可靠性]]
- [[文件、目录、inode与文件描述符]]
- [[连续、链接、索引分配与空闲空间管理]]
- [[文件系统挂载、一致性与日志]]

> [!hint]- 核心模式（点击查看）
> | 题型 | 回答路径 |
> |---|---|
> | 定义 | 对象、状态、机制、边界 |
> | 比较 | 目标、实现、开销、适用场景 |

---

## Question 1 - I-O层次 [recall]
> 设备驱动与设备控制器分别是什么？

> [!answer]- 答案
> 驱动是把通用请求翻译为设备操作的软件；控制器是管理设备寄存器、队列和传输的硬件。

---

## Question 2 - I-O语义 [recall]
> 非阻塞与异步 I/O 的核心区别是什么？

> [!answer]- 答案
> 非阻塞描述调用未就绪时立即返回；异步描述提交后由内核完成操作并通知结果。

---

## Question 3 - 三种机制 [recall]
> 缓冲、缓存和 Spooling 的主要目的分别是什么？

> [!answer]- 答案
> 匹配速度/粒度、减少重复访问、用磁盘队列虚拟共享独占设备。

---

## Question 4 - 磁盘时间 [recall]
> 机械磁盘访问时间主要由哪几部分组成？

> [!answer]- 答案
> 寻道时间、旋转延迟、传输时间以及控制器/排队开销。

---

## Question 5 - RAID容量 [recall]
> N 块等容量磁盘组成 RAID 5 的可用容量是多少？

> [!answer]- 答案
> 约为 (N-1) 块磁盘容量，可容忍一块盘故障。

---

## Question 6 - inode与fd [recall]
> inode、打开文件对象和 fd 的关系是什么？

> [!answer]- 答案
> inode描述文件；打开对象保存偏移和状态；fd 是进程表中指向打开对象的小整数索引。

---

## Question 7 - 磁盘调度 [application]
> LOOK 与 SCAN 在无请求的磁盘端点处如何不同？

> [!answer]- 答案
> LOOK 到当前方向最远请求就反向；SCAN 继续到物理端点后才反向。

---

## Question 8 - 删除文件 [application]
> 最后一个文件名被 unlink，但进程仍打开文件时数据立即释放吗？

> [!answer]- 答案
> 通常不会；链接计数归零后还要等打开引用归零，才回收 inode 和数据块。

---

## Question 9 - RAID边界 [analysis]
> 为什么 RAID 不能代替备份？

> [!answer]- 答案
> 它主要容忍部分设备故障，不能防误删、恶意修改、静默损坏以及控制器或站点级灾难。

---

## Question 10 - 日志边界 [analysis]
> 为什么启用文件系统日志后应用仍可能需要 fsync 和事务协议？

> [!answer]- 答案
> 日志首先保证文件系统结构一致，未必保证应用数据顺序、多文件原子性或 write 返回即持久化。

---

> [!summary]- 模式总结（点击查看）
> | 维度 | 检查项 |
> |---|---|
> | 正确性 | 明确状态、原子性与异常路径 |
> | 性能 | 说明时间、空间、并发和 I/O 开销 |

## Related Notes

- [[28-操作系统学习地图]]
- [[30-操作系统高频易错点]]

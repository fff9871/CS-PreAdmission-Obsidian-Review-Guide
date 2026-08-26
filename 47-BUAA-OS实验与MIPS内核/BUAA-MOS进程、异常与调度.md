---
source_pdf:
- 指导书.pdf
- 操作系统_第4章_进程概念.pdf
- 操作系统_第4章_进程调度.pdf
- Lab3实验报告.pdf
part: 实验指导书第122-148页；进程概念与调度课件；Lab3实验报告
keywords:
- operating-systems
- buaa-mos
- process
- exception-handling
---

# BUAA-MOS进程、异常与调度（★★★）

#operating-systems #buaa-mos #process-management #exception-handling #scheduling

## Overview Table

| 对象 | 作用 |
|---|---|
| Env/进程控制块 | 保存状态、优先级、页目录、Trapframe 等 |
| Trapframe | 异常发生时的寄存器现场 |
| 异常向量 | 从硬件事件进入统一保存与分派代码 |
| 就绪队列 | 保存可运行 Env |
| 调度器 | 选择下一个 Env 并恢复现场 |

## 异常到调度

    exception/interrupt
       → vector entry
       → save registers to Trapframe
       → identify cause and dispatch handler
       → maybe mark current not runnable
       → schedule next runnable Env
       → env_run / restore / eret

创建进程需分配控制块、页目录和初始用户栈，设置入口 PC 与状态寄存器。切换进程时除通用寄存器外，还要切换地址空间标识/页表和 TLB 语境。

## 调度与时钟

时钟中断提供周期性抢占点；实验调度策略常体现优先级或时间片。空就绪队列要进入安全等待或选择特殊空闲任务。

> [!warning]
> Trapframe 的布局必须与入口汇编保存顺序一致；异常返回前要检查特权级和中断位。调度队列状态与 Env 状态不一致会造成重复运行或永久丢失。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| Trapframe | 保存异常现场并作为恢复依据 |
| 时钟中断 | 记账、时间片和抢占调度入口 |
| env_run | 切换当前 Env/地址空间并恢复执行 |

## Related Notes

- [[进程状态、创建终止与上下文切换]]
- [[调度层次、评价指标与抢占]]
- [[中断、异常与陷入]]
- [[BUAA-MOS系统调用、IPC与fork]]
- [[练习-BUAA-OS实验与MIPS内核]]
- [[30-操作系统高频易错点]]

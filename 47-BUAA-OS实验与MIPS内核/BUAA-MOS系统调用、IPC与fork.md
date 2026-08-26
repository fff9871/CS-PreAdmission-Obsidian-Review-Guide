---
source_pdf:
- 指导书.pdf
- Lab4实验报告.pdf
- 计算考研复试面试常问问题 操作系统篇.pdf
part: 实验指导书第149-179页；Lab4实验报告；操作系统篇第4-8页
keywords:
- operating-systems
- buaa-mos
- system-calls
- copy-on-write
---

# BUAA-MOS系统调用、IPC与fork（★★★）

#operating-systems #buaa-mos #system-calls #ipc #copy-on-write

## Overview Table

| 机制 | 实验核心 |
|---|---|
| 系统调用 | 用户封装设置调用号/参数，陷入内核后分派并返回 |
| IPC | 接收方声明接收，发送方传值并可映射一页 |
| fork | 复制进程控制状态和地址空间视图 |
| 写时复制 | 父子先共享只读页，写异常时复制 |
| 用户级异常处理 | 内核把现场放到异常栈，跳转用户 handler |

## 系统调用路径

    user wrapper → syscall instruction
       → exception entry / Trapframe
       → syscall dispatcher
       → validate id, args, addresses, permissions
       → return value in register → eret

## COW fork

    parent writable page
       → map into parent & child as COW/read-only
       → child/parent writes
       → modification exception
       → allocate temp page + copy
       → remap faulting process writable

COW 只延迟真正发生写入的页面复制，适合 fork 后很快 exec 的场景。异常栈递归进入时需留出 Trapframe/临时字的正确空间。

> [!warning]
> 内核不能直接信任用户指针和权限；COW 页不能只改子进程，父进程原可写映射也需标记，且普通只读页不能误当 COW 复制。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| fork 返回值 | 父进程获子 PID，子进程获 0 |
| COW 触发点 | 对 COW 只读映射的首次写异常 |
| IPC 页面传递 | 传值并按权限把同一物理页映射给接收方 |

## Related Notes

- [[系统调用、API与参数传递]]
- [[进程间通信：管道、消息、共享内存与Socket]]
- [[请求分页与缺页处理]]
- [[BUAA-MOS进程、异常与调度]]
- [[BUAA-MOS文件系统、管道与Shell]]
- [[练习-BUAA-OS实验与MIPS内核]]
- [[30-操作系统高频易错点]]

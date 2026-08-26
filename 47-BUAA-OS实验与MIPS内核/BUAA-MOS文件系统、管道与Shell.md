---
source_pdf:
- 指导书.pdf
- Lab5实验报告.pdf
- Lab6实验报告.pdf
part: 实验指导书第180-214页；Lab5、Lab6实验报告
keywords:
- operating-systems
- buaa-mos
- file-system
- shell
---

# BUAA-MOS文件系统、管道与Shell（★★★）

#operating-systems #buaa-mos #file-system #pipe #shell

## Overview Table

| 模块 | 核心职责 |
|---|---|
| 磁盘块管理 | 位图分配/回收、块缓存和写回 |
| 文件元数据 | 文件大小、直接/间接块指针、目录项 |
| 文件系统服务 | 解析 IPC 请求并执行 open/read/write 等操作 |
| 文件描述符 | 用户库统一表示文件、设备和管道 |
| Pipe | 用共享页和读写位置实现字节流 |
| Shell | 解析命令，创建进程并连接重定向/管道 |

## 文件请求路径

    user fd API
       → device/file operation table
       → IPC to file-system server
       → block cache / bitmap / file metadata
       → disk I/O

## Shell 管道

    command A stdout → pipe write end
                           shared buffer
    command B stdin  ← pipe read end

Shell 要正确处理 fork/spawn、参数、环境、输入输出重定向、管道两端关闭与子进程回收。若无关进程仍持有写端，读者可能永远看不到 EOF。

## 一致性检查

位图、文件大小、块指针、缓存脏状态和磁盘写回顺序应一致；边界测试包括空文件、跨块读写、间接块、磁盘满、重复关闭和管道环绕。

> [!warning]
> 管道是字节流，不保留命令输出的应用消息边界；关闭 fd 只是减少引用，只有所有写端引用关闭后读端才得到 EOF。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 文件系统服务为何用 IPC | 把文件服务放在用户态并通过统一请求协议隔离 |
| 管道 EOF | 所有写端引用关闭且缓冲读空 |
| Shell 管道关键 | 创建管道、重定向 fd、关闭无关端点、并发运行子命令 |

## Related Notes

- [[文件、目录、inode与文件描述符]]
- [[文件系统挂载、一致性与日志]]
- [[进程间通信：管道、消息、共享内存与Socket]]
- [[BUAA-MOS系统调用、IPC与fork]]
- [[练习-BUAA-OS实验与MIPS内核]]
- [[30-操作系统高频易错点]]

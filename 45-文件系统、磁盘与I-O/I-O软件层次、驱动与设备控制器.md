---
source_pdf:
- 操作系统_第5章_IO_wty_2021.pdf
- 计算考研复试面试常问问题 操作系统篇.pdf
- 指导书.pdf
part: I/O课件第1-87页；操作系统篇第15-17页；实验指导书第180-197页
keywords:
- operating-systems
- io-management
- device-driver
- device-controller
---

# I-O软件层次、驱动与设备控制器（★★★）

#operating-systems #io-management #device-driver #device-controller

## Overview Table

| 层次 | 主要职责 |
|---|---|
| 用户 I/O 库 | 格式化、缓冲、API 封装 |
| 设备无关软件 | 命名、权限、统一接口、分配、错误报告 |
| 设备驱动 | 把通用请求翻译为设备命令 |
| 中断处理 | 响应完成/错误并唤醒等待者 |
| 控制器与设备 | 寄存器、队列、DMA 和物理传输 |

## 请求路径

    app read/write
       ↓ system call / VFS
    block/char layer → driver → controller → device
       ↑ completion interrupt / polling / DMA
    wakeup → copy/map result → app

字符设备通常提供字节流或记录接口；块设备按可寻址块读写并支持缓存。驱动负责设备特性，设备无关层提供统一抽象。

## 控制方式

程序查询让 CPU 忙等；中断驱动在设备就绪时通知 CPU；DMA 让控制器直接传输内存块，CPU 负责配置和完成处理。

> [!warning]
> 驱动不等于控制器：驱动是软件，控制器是硬件。DMA 也不是完全脱离 CPU，它仍需初始化、映射、同步和完成中断处理。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 设备无关性 | 上层使用统一接口，差异封装在驱动 |
| 中断作用 | 通知完成/错误，避免持续轮询 |
| DMA 作用 | 设备与内存间块传输，减少 CPU 搬运 |

## Related Notes

- [[阻塞非阻塞、同步异步与I-O多路复用]]
- [[缓冲、缓存、假脱机与设备分配]]
- [[程序查询与中断驱动I-O]]
- [[DMA传送与I-O通道]]
- [[练习-文件系统、磁盘与I-O]]
- [[30-操作系统高频易错点]]

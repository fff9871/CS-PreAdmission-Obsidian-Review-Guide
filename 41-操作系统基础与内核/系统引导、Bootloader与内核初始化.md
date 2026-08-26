---
source_pdf:
- 操作系统_第2章_系统引导_wty_2022.pdf
- 指导书.pdf
- OS预习指导.pdf
- 预习指导（补充）.pdf
part: 系统引导课件第1-94页；实验指导书第61-96页；预习指导
keywords:
- operating-systems
- boot-process
- bootloader
- kernel-initialization
---

# 系统引导、Bootloader与内核初始化（★★★）

#operating-systems #os-fundamentals #boot-process

## Overview Table

| 阶段 | 主要任务 |
|---|---|
| 固件 | 上电自检、初始化最小硬件、选择启动设备 |
| Bootloader | 读取内核映像、准备参数和内存、转移控制权 |
| 内核早期初始化 | 建立栈、页表、异常向量和基本设备环境 |
| 内核子系统初始化 | 内存、调度、驱动、文件系统和中断 |
| 用户空间启动 | 挂载根文件系统，启动 init/system manager 与服务 |

## 典型路径

    Reset Vector → Firmware/BIOS/UEFI
       → Bootloader → Load Kernel/Initramfs
       → Kernel Entry → MMU/Interrupt/Memory/Driver Init
       → Root FS → init → services/login

Bootloader 需要理解映像格式和加载地址；链接脚本决定段布局与符号，ELF 程序头描述需装载的段。

## 启动优化

可通过并行初始化、延迟加载驱动、减少探测和服务、缓存设备信息、优化存储读取等缩短启动时间，但必须保留依赖关系和故障恢复。

> [!warning]
> x86 BIOS/UEFI、嵌入式固件和 MIPS 模拟器启动细节不同。面试先回答通用链路，再结合平台说明入口地址、Bootloader 和映像格式。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| 上电到用户程序 | 固件→引导器→内核初始化→根文件系统→init |
| Bootloader 作用 | 定位/装载内核、准备环境并跳转入口 |
| ELF 与链接脚本 | 描述段及加载信息、控制内核地址布局 |

## Related Notes

- [[BUAA-MOS实验环境、构建与GXemul]]
- [[BUAA-MOS启动、ELF与链接脚本]]
- [[用户态、内核态与特权指令]]
- [[练习-操作系统基础与内核]]
- [[30-操作系统高频易错点]]

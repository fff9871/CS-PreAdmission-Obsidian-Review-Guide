---
source_pdf:
- 指导书.pdf
- 操作系统_第2章_系统引导_wty_2022.pdf
- Lab1实验报告.pdf
part: 实验指导书第61-96页；系统引导课件第1-94页；Lab1实验报告
keywords:
- operating-systems
- buaa-mos
- elf
- linker-script
---

# BUAA-MOS启动、ELF与链接脚本（★★★）

#operating-systems #buaa-mos #boot-process #elf #linker-script

## Overview Table

| 对象 | 作用 |
|---|---|
| ELF Header | 文件类型、目标架构、入口和表位置 |
| Program Header | 装载器需要的段、地址、大小和权限 |
| Section Header | 链接/调试视角的 section 元数据 |
| 链接脚本 | 规定 section 合并、虚拟/装载地址和关键符号 |
| 启动汇编 | 建栈、清 BSS、准备早期环境并进入 C 代码 |

## 启动路径

    GXemul/firmware
       → load ELF PT_LOAD segments
       → jump ELF entry
       → start.S: stack/BSS/CP0 basics
       → mips_init / kernel C entry
       → memory, exception, process subsystems

ELF 的 section 面向链接，segment 面向运行时装载；多个 section 可组合到一个可装载 segment。`memsz > filesz` 的尾部通常对应需零初始化的 BSS。

## VMA 与 LMA

VMA 是运行时虚拟地址，LMA 是映像装载地址；内核可能在物理低地址装入，却按高虚拟地址链接并运行，需由启动代码和地址转换约定配合。

> [!warning]
> ELF entry 只是第一条控制转移目标，不自动完成栈、页表和全局变量初始化；section 不一定都出现在最终内存映像中。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| Program vs Section Header | 装载视图 vs 链接/调试视图 |
| BSS 为何不占等量文件空间 | 只记录内存大小，装载时零填充 |
| 链接脚本 | 控制布局、地址、入口与导出符号 |

## Related Notes

- [[BUAA-MOS实验环境、构建与GXemul]]
- [[BUAA-MOS物理内存、页表与TLB重填]]
- [[系统引导、Bootloader与内核初始化]]
- [[练习-BUAA-OS实验与MIPS内核]]
- [[30-操作系统高频易错点]]

---
source_pdf:
- 指导书.pdf
- OS预习指导.pdf
- 预习指导（补充）.pdf
- Lab0实验报告.pdf
part: 实验指导书第1-60页；预习指导；Lab0实验报告
keywords:
- operating-systems
- buaa-mos
- toolchain
- gxemul
---

# BUAA-MOS实验环境、构建与GXemul（★★★）

#operating-systems #buaa-mos #toolchain #gxemul

## Overview Table

| 组件 | 作用 |
|---|---|
| MIPS 交叉工具链 | 在宿主机生成 MIPS 目标文件和内核映像 |
| Makefile | 描述编译、链接、依赖和运行目标 |
| GXemul | 模拟 MIPS 机器并加载内核 |
| GDB/objdump/readelf | 调试、反汇编和检查 ELF |
| Git | 保存实验增量和分支历史 |

## 构建链路

    .S/.c source
       → preprocessor/compiler/assembler
       → .o relocatable objects
       → linker + linker script
       → ELF kernel image
       → GXemul load/run

`make` 根据目标、依赖和时间戳决定命令；交叉编译器的 target 是 MIPS，而 host 是开发机。反汇编用于把机器码与源代码/符号对应。

## 调试顺序

1. 确认工具链前缀、PATH 和版本。
2. 清理并重新构建，先看最早的错误。
3. 用 `readelf/objdump` 检查入口、段和符号。
4. 查看 GXemul 启动参数与串口输出。
5. 在关键入口设置断点或加入最小日志。

> [!warning]
> 宿主可执行文件与 MIPS 目标文件不能混用；构建成功只说明语法和链接闭合，不代表装载地址、ABI 和运行时状态正确。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 为什么交叉编译 | 构建平台与运行 ISA 不同 |
| Makefile 核心 | 目标、依赖、命令与变量 |
| GXemul 作用 | 模拟目标 MIPS 机器并运行内核映像 |

## Related Notes

- [[BUAA-MOS启动、ELF与链接脚本]]
- [[系统引导、Bootloader与内核初始化]]
- [[MIPS-C指令分类与RISC实例]]
- [[练习-BUAA-OS实验与MIPS内核]]
- [[30-操作系统高频易错点]]

---
source_pdf:
- MIPS-C指令集_校对完成版_-指令排序.pdf
- MIPS_Vol2_指令集_.pdf
- IDT R30xx Family Software Reference Manual.pdf
part: MIPS-C第1-8页及指令详解；MIPS Vol2第18-20页；IDT R30xx手册第13-25、214页
keywords:
- computer-organization
- mips
- risc
- instruction-format
---

# MIPS-C指令分类与RISC实例（★★★）

#computer-organization #instruction-set #risc #mips

## Overview Table

| MIPS-C 类别 | 代表指令 | 语义 |
|---|---|---|
| 加载 | `LB/LBU/LH/LHU/LW` | 主存到通用寄存器 |
| 保存 | `SB/SH/SW` | 通用寄存器到主存 |
| R-R 运算 | `ADD/SUB/AND/OR/SLT` | 寄存器间运算 |
| R-I 运算 | `ADDI/ANDI/ORI/LUI` | 寄存器与立即数运算 |
| 分支 | `BEQ/BNE/BLTZ/BGEZ` | 条件改变 PC |
| 跳转 | `J/JAL/JR/JALR` | 无条件控制转移/过程调用 |
| 传输 | `MFHI/MFLO/MTHI/MTLO` | 通用寄存器与 HI/LO 间传送 |
| 特权 | `MFC0/MTC0/ERET` | 访问 CP0、异常返回 |
| 陷阱 | `BREAK/SYSCALL` | 产生异常进入系统处理 |

## 三类基本编码

| 格式 | 典型字段 | 用途 |
|---|---|---|
| R 型 | opcode、rs、rt、rd、shamt、funct | 寄存器运算 |
| I 型 | opcode、rs、rt、immediate | 立即数、访存、条件分支 |
| J 型 | opcode、target | 跳转 |

    lw  rt, offset(rs)
    EA = GPR[rs] + sign_extend(offset)
    GPR[rt] ← Mem[EA]

## RISC 特征在 MIPS 中的体现

- 固定长度、规则字段，便于取指与译码。
- Load/Store：只有加载和保存直接访问主存。
- 大量通用寄存器，三操作数寄存器运算常见。
- 分支和跳转明确控制 PC，异常通过 CP0/EPC 等状态支持。

> [!warning]
> `ADDIU` 名称中的“无符号”主要表示不触发有符号溢出异常，立即数仍进行符号扩展；不能简单理解为完全按无符号数运算。具体延迟槽和异常行为还取决于 MIPS 版本与实现。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| Load/Store | 算术只操作寄存器，主存通过 load/store 访问 |
| `JAL` | 跳转并保存返回地址 |
| `SYSCALL/ERET` | 进入异常处理/从异常返回 |

## Related Notes

- [[26-计算机组成高频易错点]]
- [[指令格式、操作码与地址码]]
- [[寻址方式与有效地址计算]]
- [[CISC与RISC]]
- [[控制器、硬布线与微程序控制]]
- [[练习-指令系统与CPU]]

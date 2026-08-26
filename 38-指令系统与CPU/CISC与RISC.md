---
source_pdf:
- 计算机考研复试面试常问问题 计算机组成原理篇.pdf
- 专业课程基础概念复习.pdf
- IDT R30xx Family Software Reference Manual.pdf
part: 组成原理篇第11-12页；基础概念第14页；IDT R30xx手册第13-25页
keywords:
- computer-organization
- cisc
- risc
- instruction-set
---

# CISC与RISC（★★★）

#computer-organization #instruction-set #cisc #risc

## Overview Table

| 维度 | CISC 倾向 | RISC 倾向 |
|---|---|---|
| 指令 | 数量多、功能复杂、长度可变 | 数量较少、操作规则、常定长 |
| 访存 | 多种指令可访存 | Load/Store 架构，算术多在寄存器间 |
| 寻址 | 方式丰富 | 较少且规则 |
| 控制 | 历史上常见微程序控制 | 历史上偏硬布线与快速译码 |
| 流水线 | 复杂译码增加难度 | 规则格式便于流水化 |
| 代码密度 | 往往较高 | 可能需要更多简单指令 |

## 设计取舍

RISC 把复杂工作更多交给编译器，用大量通用寄存器和规则指令提高流水效率；CISC 通过丰富指令提高表达力和代码密度。现代处理器边界已模糊：复杂 ISA 可译成内部微操作，RISC ISA 也不断扩展。

    高级语言
       ↓ 编译器调度/寄存器分配
    ISA 指令
       ↓ 前端译码
    微体系结构执行资源

## CPI 与指令数

不能只比较 CPI。RISC 可能 CPI 较低但指令数较多；CISC 单条指令工作量大但译码复杂。最终仍应比较 `IC × CPI × T`。

> [!warning]
> RISC 不等于“指令一定少”，CISC 也不等于“没有流水线”。这些标签描述设计倾向，不应机械判断现代 CPU 的实现。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| Load/Store、定长、寄存器多 | RISC 倾向 |
| 复杂寻址、变长、代码密度 | CISC 倾向 |
| 谁一定更快 | 不能仅凭 ISA 类型判断，需看实现和工作负载 |

## Related Notes

- [[26-计算机组成高频易错点]]
- [[MIPS-C指令分类与RISC实例]]
- [[指令流水线原理与性能]]
- [[CPU性能指标、CPI与阿姆达尔定律]]
- [[练习-指令系统与CPU]]

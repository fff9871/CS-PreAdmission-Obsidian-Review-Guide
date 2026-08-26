---
source_pdf:
- 计算机考研复试面试常问问题 计算机组成原理篇.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
part: 组成原理篇第8-9页；精品综合题第29页
keywords:
- computer-organization
- semiconductor-memory
- sram
- dram
- rom
---

# SRAM、DRAM与ROM（★★★）

#computer-organization #memory-hierarchy #semiconductor-memory #sram #dram #rom

## Overview Table

| 类型 | 存储单元/刷新 | 速度与密度 | 典型用途 |
|---|---|---|---|
| SRAM | 双稳态触发器，不需刷新 | 快、密度低、成本高 | Cache |
| DRAM | 电容电荷，需周期刷新 | 较慢、密度高、成本低 | 主存 |
| ROM | 非易失，读取为主 | 断电保存 | 固件、启动代码 |
| Flash | 可电擦写非易失存储 | 擦写粒度和寿命受限 | SSD、固件存储 |

## DRAM 访问

DRAM 芯片常把地址分为行、列两次送入，以减少地址引脚。访问先激活行到行缓冲，再选择列；刷新会占用存储阵列时间。

    行地址 → RAS/激活 → 行缓冲
    列地址 → CAS/选择 → 数据传输

## ROM 家族

- Mask ROM：制造时写入。
- PROM：一次可编程。
- EPROM：紫外线擦除。
- EEPROM/Flash：电擦写，Flash 通常按块擦除。

> [!warning]
> SRAM/DRAM 都是随机存取、易失性存储器；“动态”指电荷需要刷新，不表示它只能动态分配。ROM 也不一定绝对不可写，需区分具体器件。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| Cache 用什么 | SRAM，速度快但面积和成本高 |
| 主存用什么 | DRAM，密度高但需刷新 |
| 断电保存 | ROM/Flash 等非易失存储 |

## Related Notes

- [[26-计算机组成高频易错点]]
- [[存储层次与局部性]]
- [[主存编址、扩展与多模块交叉]]
- [[Cache结构、命中率与平均访问时间]]
- [[练习-存储系统与Cache]]

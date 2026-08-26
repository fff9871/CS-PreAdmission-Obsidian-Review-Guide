---
source_pdf:
- 计算机考研复试面试常问问题 计算机组成原理篇.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
part: 组成原理篇第9-10页；精品综合题第29-30页
keywords:
- computer-organization
- cache-mapping
- direct-mapped
- set-associative
---

# Cache映射方式（★★★）

#computer-organization #memory-hierarchy #cache #cache-mapping

## Overview Table

| 映射 | 主存块可放位置 | 查找硬件 | 冲突缺失 |
|---|---|---|---|
| 直接映射 | 唯一一行 | 最简单，只比较一个 Tag | 最多 |
| 全相联 | 任意行 | 并行比较所有 Tag | 最少，成本高 |
| 组相联 | 指定组内任意一路 | 组内并行比较 | 折中 |

## 计算关系

设 Cache 有 C 个块、每组 E 路，则组数 `S=C/E`。主存块号 `B` 映射到：

- 直接映射行号：`B mod C`
- E 路组相联组号：`B mod S`
- 全相联：无固定 index，任意行

    主存块号 B
       ↓ mod 组数
    选中一组 ─→ 并行比较 E 个 Tag

## 三类缺失

| 缺失 | 原因 | 改善思路 |
|---|---|---|
| 强制缺失 | 第一次访问块 | 预取、适当增大块 |
| 容量缺失 | 工作集超过 Cache | 增大容量、改善局部性 |
| 冲突缺失 | 多块竞争同一组 | 提高相联度、改变布局 |

> [!warning]
> 提高相联度通常减少冲突缺失，但会增加比较器数量、功耗和可能的命中延迟；并非路数越高越好。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| 主存块只能固定位置 | 直接映射 |
| 组内任意一路 | 组相联 |
| 不需要 index | 全相联 |

## Related Notes

- [[Cache结构、命中率与平均访问时间]]
- [[Cache替换算法与写策略]]
- [[练习-存储系统与Cache]]
- [[26-计算机组成高频易错点]]

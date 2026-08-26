---
source_pdf:
- 操作系统_第3章_内存管理（5）_wty_2022.pdf
- 操作系统_第3章_内存管理（6）_wty_2022.pdf
- 操作系统_总复习_wty_2022_with作业答案.pdf
part: 内存管理课件（5）第1-60页、（6）第1-44页；总复习页面置换章节
keywords:
- operating-systems
- virtual-memory
- page-replacement
- lru
---

# FIFO、LRU、CLOCK与Belady异常（★★★）

#operating-systems #memory-management #virtual-memory #page-replacement #lru

## Overview Table

| 算法 | 依据 | 特点 |
|---|---|---|
| OPT | 最晚未来再访问 | 理论下界，只能离线比较 |
| FIFO | 最早进入内存 | 简单，可能出现 Belady 异常 |
| LRU | 最久未访问 | 利用时间局部性，精确实现成本高 |
| CLOCK | 访问位 + 循环指针 | LRU 的常用近似 |
| LFU | 历史频率 | 可能保留早期热门但已冷却页面 |

## 手算方法

1. 固定页框数，按引用串逐项推进。
2. 命中只更新算法状态；未命中计一次缺页。
3. 页框满后按规则选择牺牲页。
4. 分别记录页框内容、访问位/时间戳和缺页次数。

Belady 异常指增加页框反而使缺页数增加，FIFO 可能发生；OPT、LRU 等栈算法具有包含性，不发生该异常。

## CLOCK

指针遇访问位 1 时清零并跳过，遇 0 时替换；增强 CLOCK 还综合脏位，优先选择未访问且干净的页。

> [!warning]
> “最近使用”与“进入内存最早”不同；题目中发生命中时 LRU 顺序必须更新，而 FIFO 队列通常不变。

## Exam/Test Patterns

| 问法 | 答案 |
|---|---|
| 理论最少缺页 | OPT |
| Belady 异常 | FIFO 可能，LRU/OPT 不会 |
| 工程近似 LRU | CLOCK/Second Chance |

## Related Notes

- [[请求分页与缺页处理]]
- [[工作集、驻留集与抖动]]
- [[Cache替换算法与写策略]]
- [[练习-内存管理与虚拟存储]]
- [[30-操作系统高频易错点]]

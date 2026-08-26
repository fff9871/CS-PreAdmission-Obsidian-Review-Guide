---
source_pdf:
- 操作系统_第3章_内存管理（3）_wty_2022.pdf
- 操作系统_第3章_内存管理（4）_wty_2022.pdf
- 计算考研复试面试常问问题 操作系统篇.pdf
- 指导书.pdf
part: 内存管理课件（3）第1-54页、（4）第1-69页；操作系统篇第11-14页；实验指导书第97-121页
keywords:
- operating-systems
- memory-management
- tlb
- effective-access-time
---

# TLB、有效访问时间与缺页边界（★★★）

#operating-systems #memory-management #paging #tlb

## Overview Table

| 事件 | 含义 | 后续 |
|---|---|---|
| TLB hit | 缓存中找到地址翻译 | 直接形成物理地址 |
| TLB miss | 缓存中无翻译 | 硬件或软件遍历页表 |
| Page fault | 页表表明目标页不在主存/映射未满足 | 陷入内核处理 |
| Protection fault | 页面存在但权限不允许 | 拒绝、信号或 COW 等处理 |

## 有效访问时间

在简化单级页表模型中，TLB 查找时间 `ε`、内存时间 `m`、命中率 `α`：

`EAT = α(ε+m) + (1-α)(ε+2m)`

若 TLB 与 Cache 并行、页表多级或考虑缺页概率，公式必须按实际访问路径重新建立。

    VA → TLB hit ─────────────→ PA
          └ miss → page walk ─→ fill TLB → PA
                         └ not present → page fault

ASID/PCID 可区分不同地址空间的 TLB 项，减少进程切换时全量刷新。修改映射后需失效相关条目。

> [!warning]
> TLB miss 不等于缺页，Cache miss 也不等于 TLB miss。TLB 缓存的是地址翻译，Cache 缓存的是数据/指令块。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| TLB 未命中 | 查页表，页面可能已驻留 |
| 缺页 | 需内核建立/恢复映射，可能访问磁盘 |
| EAT | 对每条完整访问路径按概率加权 |

## Related Notes

- [[分页、页表与地址转换]]
- [[请求分页与缺页处理]]
- [[虚拟存储、页表与TLB]]
- [[BUAA-MOS物理内存、页表与TLB重填]]
- [[练习-内存管理与虚拟存储]]
- [[30-操作系统高频易错点]]

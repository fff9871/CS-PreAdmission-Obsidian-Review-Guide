---
source_pdf:
- 指导书.pdf
- 操作系统_第3章_内存管理（3）_wty_2022.pdf
- 操作系统_第3章_内存管理（7）_自映射_wty_2022.pdf
- Lab2实验报告.pdf
part: 实验指导书第97-121页；内存管理课件（3）及（7）；Lab2实验报告
keywords:
- operating-systems
- buaa-mos
- physical-memory
- tlb-refill
---

# BUAA-MOS物理内存、页表与TLB重填（★★★）

#operating-systems #buaa-mos #memory-management #page-table #tlb-refill

## Overview Table

| 模块 | 任务 |
|---|---|
| 物理页管理 | 初始化 Page 数组、空闲链表、分配/回收页 |
| 页表管理 | 建立页目录/页表、插入、查询和删除映射 |
| 地址宏 | 在物理地址、内核虚拟地址、页号和 Page 间转换 |
| TLB 重填 | TLB miss 时查页表并写入匹配项 |

## 映射建立

    page_alloc → physical Page
       → pgdir_walk(create page table if needed)
       → write PTE(frame + permission)
       → invalidate/update TLB when replacing mapping

页的引用计数用于判断物理页是否仍被映射；替换已有映射时要处理旧页引用并维护 TLB。页表页本身也来自物理页分配器。

## MIPS TLB 路径

    virtual access → TLB lookup
       ├ hit + permission → physical access
       └ miss/invalid/mod → exception
              → software reads page table
              → EntryHi/EntryLo/Index or Random
              → tlb write → retry

不同异常区分“未命中/无效”和“写只读页”等情况，异常入口必须保存足够现场。

> [!warning]
> PTE 更新后旧 TLB 项可能仍有效；引用计数、页表项和空闲链表必须作为一个一致性协议维护，不能只修改其中一处。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| pgdir_walk | 查找 PTE，必要时创建下级页表 |
| 映射替换 | 失效 TLB、降低旧页引用、建立新 PTE |
| MIPS TLB miss | 软件异常处理程序查页表并重填 |

## Related Notes

- [[分页、页表与地址转换]]
- [[多级页表、反置页表与页表自映射]]
- [[TLB、有效访问时间与缺页边界]]
- [[BUAA-MOS进程、异常与调度]]
- [[练习-BUAA-OS实验与MIPS内核]]
- [[30-操作系统高频易错点]]

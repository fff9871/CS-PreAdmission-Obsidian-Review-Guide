---
source_pdf:
- 操作系统_第6章_磁盘管理_wty_2021.pdf
- 计算考研复试面试常问问题 操作系统篇.pdf
part: 磁盘管理课件第1-96页；操作系统篇第15-17页
keywords:
- operating-systems
- storage-management
- raid
- fault-tolerance
---

# RAID级别、容量与可靠性（★★★）

#operating-systems #storage-management #raid #fault-tolerance

## Overview Table

| RAID | 布局 | 可用容量（N块等容量盘） | 容错 |
|---|---|---:|---|
| 0 | 条带化 | `N×S` | 无 |
| 1 | 镜像 | 典型 `N/2×S` | 每镜像组可坏一块 |
| 4 | 块条带 + 专用校验盘 | `(N-1)×S` | 一块 |
| 5 | 块条带 + 分布式校验 | `(N-1)×S` | 一块 |
| 6 | 双重分布式校验 | `(N-2)×S` | 两块 |
| 10 | 先镜像后条带 | 典型 `N/2×S` | 取决于故障分布 |

RAID 0 提高并行吞吐但没有冗余；RAID 5 小写常需读—改—写校验；重建期间性能下降且第二故障风险上升。

## 写入路径

    data update + old parity/data
        → compute new parity
        → write data + parity

全条带写可避免部分读—改—写。控制器缓存需断电保护，否则确认写入后仍可能丢失。

> [!warning]
> RAID 提供可用性与部分故障容忍，不是备份：误删、勒索、静默损坏和控制器/站点故障仍需独立备份与校验。

## Exam/Test Patterns

| 需求 | 常见选择 |
|---|---|
| 最大容量/吞吐且可丢失 | RAID 0 |
| 简单低延迟冗余 | RAID 1/10 |
| 单盘校验容错 | RAID 5 |
| 双盘容错 | RAID 6 |

## Related Notes

- [[磁盘结构、寻道与格式化]]
- [[FCFS、SSTF、SCAN与C-SCAN磁盘调度]]
- [[文件系统挂载、一致性与日志]]
- [[练习-文件系统、磁盘与I-O]]
- [[30-操作系统高频易错点]]

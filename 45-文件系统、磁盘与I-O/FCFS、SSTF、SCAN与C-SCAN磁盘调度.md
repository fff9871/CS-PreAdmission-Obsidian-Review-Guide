---
source_pdf:
- 操作系统_第6章_磁盘管理_wty_2021.pdf
- 操作系统_总复习_wty_2022_with作业答案.pdf
part: 磁盘管理课件第1-96页；总复习磁盘调度章节
keywords:
- operating-systems
- storage-management
- disk-scheduling
- scan
---

# FCFS、SSTF、SCAN与C-SCAN磁盘调度（★★★）

#operating-systems #storage-management #disk-scheduling #scan

## Overview Table

| 算法 | 规则 | 特点 |
|---|---|---|
| FCFS | 到达顺序 | 公平简单，移动距离可能大 |
| SSTF | 最近请求先服务 | 平均寻道较小，远端请求可能饥饿 |
| SCAN | 沿一方向服务至端点再反向 | 电梯式，等待较稳定 |
| LOOK | 只走到该方向最远请求再反向 | 减少无请求端点移动 |
| C-SCAN | 单向服务，到端后快速回起点 | 等待时间更均匀 |
| C-LOOK | 单向走到最远请求后跳到另一端请求 | C-SCAN 的 LOOK 版本 |

## 手算流程

1. 标出初始磁头和当前移动方向。
2. 依算法写服务序列，区分“磁盘端点”与“最远请求”。
3. 总移动量为相邻位置差绝对值之和。

    0 ─── requests ─── head → ─── requests ─── max
         SCAN 到端反向；LOOK 到最远请求即反向

> [!warning]
> SCAN/C-SCAN 必须知道初始方向；是否计入回程以及磁道范围要按题目定义。SSTF 每服务一个请求后都要从新位置重新选择最近者。

## Exam/Test Patterns

| 关键词 | 答案 |
|---|---|
| 最近请求 | SSTF |
| 双向电梯 | SCAN/LOOK |
| 单向均匀等待 | C-SCAN/C-LOOK |

## Related Notes

- [[磁盘结构、寻道与格式化]]
- [[RAID级别、容量与可靠性]]
- [[调度层次、评价指标与抢占]]
- [[练习-文件系统、磁盘与I-O]]
- [[30-操作系统高频易错点]]

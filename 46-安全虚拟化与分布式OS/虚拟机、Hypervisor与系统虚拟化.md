---
source_pdf:
- 操作系统_第1章_引论_wty_2022.pdf
- 操作系统_第八章_安全_wty.pdf
- 计算考研复试面试常问问题 操作系统篇.pdf
part: 引论课件虚拟机章节；安全课件虚拟化相关内容；操作系统篇第2、17页
keywords:
- operating-systems
- virtualization
- virtual-machines
- hypervisor
---

# 虚拟机、Hypervisor与系统虚拟化（★★★）

#operating-systems #virtualization #virtual-machines #hypervisor

## Overview Table

| 类型 | 位置 | 特点 |
|---|---|---|
| Type 1 Hypervisor | 裸机硬件之上 | 隔离和控制直接，常用于服务器 |
| Type 2 Hypervisor | 宿主 OS 之上 | 易用，依赖宿主调度和驱动 |
| 全虚拟化 | 客体可不修改 | 依靠硬件辅助或指令模拟 |
| 半虚拟化 | 客体通过 hypercall 配合 | 可减少模拟开销，需适配 |
| 模拟器 | 模拟不同 ISA/整机 | 兼容性强，通常更慢 |

## 核心虚拟化

    guest app → guest OS
                    ↓ privileged op / trap / hypercall
                 hypervisor
                    ↓
             CPU / memory / devices

CPU 借助陷入与硬件虚拟化扩展；内存常用影子页表或二阶段地址转换；I/O 可通过模拟、半虚拟驱动或设备直通。

## 隔离与资源管理

Hypervisor 管理 vCPU 调度、内存超分、虚拟设备、快照与迁移。VM 边界较强，但共享 Hypervisor、硬件和侧信道仍是风险。

> [!warning]
> 虚拟机不是模拟器的同义词；Type 2 也不表示客体“没有隔离”。快照不是长期备份，恢复快照还会回滚系统时间和外部状态视图。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| Type 1 vs Type 2 | 裸机直接运行 vs 依赖宿主 OS |
| 内存虚拟化 | 客体 VA→客体 PA→宿主 PA 的二阶段转换 |
| hypercall | 客体主动请求 Hypervisor 服务 |

## Related Notes

- [[容器、Namespace与Cgroup]]
- [[单体内核、微内核与模块化结构]]
- [[地址空间、重定位与地址映射]]
- [[练习-安全虚拟化与分布式OS]]
- [[30-操作系统高频易错点]]

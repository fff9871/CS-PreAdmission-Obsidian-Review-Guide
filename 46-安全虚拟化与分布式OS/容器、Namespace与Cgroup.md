---
source_pdf:
- 操作系统_第1章_引论_wty_2022.pdf
- 操作系统_第八章_安全_wty.pdf
part: 引论课件虚拟化章节；安全课件隔离相关内容
keywords:
- operating-systems
- virtualization
- containers
- cgroups
---

# 容器、Namespace与Cgroup（★★★）

#operating-systems #virtualization #containers #cgroups

## Overview Table

| 机制 | 作用 |
|---|---|
| Namespace | 隔离进程可见的 PID、挂载、网络、IPC、用户等资源视图 |
| Cgroup | 统计、限制和调度 CPU、内存、I/O 等资源 |
| Capability | 拆分传统超级用户特权 |
| Seccomp | 过滤可用系统调用 |
| Union/Overlay FS | 叠加只读镜像层和可写层 |

## 与虚拟机比较

| 维度 | 容器 | 虚拟机 |
|---|---|---|
| 内核 | 共享宿主内核 | 客体自带内核 |
| 启动与密度 | 快、密度高 | 相对重 |
| 内核隔离边界 | 依赖同一内核机制 | Hypervisor/硬件边界通常更强 |
| OS 多样性 | 受宿主内核约束 | 可运行不同客体 OS |

    container processes
       → namespaces + cgroups + LSM/seccomp
       → shared host kernel
       → hardware

rootless 容器可用用户命名空间降低宿主风险；镜像签名、最小镜像、只读根和敏感挂载控制属于运行时加固。

> [!warning]
> 容器不是轻量虚拟机的严格同义词，它隔离的是进程视图并共享内核；namespace 负责“看见什么”，cgroup 负责“能用多少”。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| Namespace | 资源视图隔离 |
| Cgroup | 资源计量、限制和调度 |
| 容器 vs VM | 共享宿主内核 vs 客体独立内核 |

## Related Notes

- [[虚拟机、Hypervisor与系统虚拟化]]
- [[身份认证、授权与访问控制]]
- [[调度层次、评价指标与抢占]]
- [[练习-安全虚拟化与分布式OS]]
- [[30-操作系统高频易错点]]

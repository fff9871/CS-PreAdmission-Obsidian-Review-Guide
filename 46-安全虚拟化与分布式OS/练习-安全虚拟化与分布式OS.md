---
source_pdf:
- 操作系统_第八章_安全_wty.pdf
- 操作系统_第九章_分布式OS_wty.pdf
- 操作系统_第1章_引论_wty_2022.pdf
- 计算考研复试面试常问问题 操作系统篇.pdf
part: 认证授权、访问控制、安全、虚拟化、容器与分布式系统
keywords:
- practice
- operating-systems
- system-security
---

# 安全虚拟化与分布式OS Practice（10 questions）

#practice #operating-systems #system-security

## Related Concepts

- [[身份认证、授权与访问控制]]
- [[DAC、MAC、RBAC与能力表]]
- [[安全威胁、恶意软件与系统加固]]
- [[虚拟机、Hypervisor与系统虚拟化]]
- [[容器、Namespace与Cgroup]]
- [[分布式系统目标、透明性与体系结构]]
- [[RPC、RMI与分布式通信]]
- [[分布式文件系统、一致性与容错]]
- [[分布式共享内存与进程迁移]]

> [!hint]- 核心模式（点击查看）
> | 题型 | 回答路径 |
> |---|---|
> | 定义 | 对象、状态、机制、边界 |
> | 比较 | 目标、实现、开销、适用场景 |

---

## Question 1 - 认证授权 [recall]
> 认证与授权分别回答什么问题？

> [!answer]- 答案
> 认证证明主体是谁；授权判断该主体是否可对对象执行某操作。

---

## Question 2 - 访问模型 [recall]
> DAC、MAC 与 RBAC 的授权依据分别是什么？

> [!answer]- 答案
> 对象所有者决定、强制安全标签策略、以及用户所属角色。

---

## Question 3 - 恶意软件 [recall]
> 病毒与蠕虫的传播方式有何不同？

> [!answer]- 答案
> 病毒通常依附宿主文件或程序；蠕虫可利用网络和漏洞自主传播。

---

## Question 4 - Hypervisor [recall]
> Type 1 与 Type 2 Hypervisor 的位置有何不同？

> [!answer]- 答案
> Type 1 直接运行在硬件上；Type 2 运行在宿主操作系统之上。

---

## Question 5 - 容器机制 [recall]
> namespace 与 cgroup 分别解决什么问题？

> [!answer]- 答案
> namespace 隔离资源视图；cgroup 计量、限制和调度资源使用。

---

## Question 6 - RPC语义 [recall]
> RPC 超时能否证明服务端未执行请求？

> [!answer]- 答案
> 不能。请求或回复可能在网络中丢失，执行结果可能未知。

---

## Question 7 - 权限设计 [application]
> 给临时运维人员授权时如何贯彻最小权限？

> [!answer]- 答案
> 只授予任务所需资源和操作，设置最短有效期，启用强认证和审计，到期自动撤销。

---

## Question 8 - 重试设计 [application]
> 支付类 RPC 如何避免超时重试造成重复扣款？

> [!answer]- 答案
> 使用全局请求 ID、持久化去重、幂等状态转换或事务性条件写。

---

## Question 9 - 容器隔离 [analysis]
> 为什么容器启动快、密度高，但通常不能直接等同于虚拟机隔离？

> [!answer]- 答案
> 容器共享宿主内核，只隔离进程资源视图；虚拟机有独立客体内核和 Hypervisor/硬件边界。

---

## Question 10 - 透明性边界 [analysis]
> 为什么分布式系统不应把所有网络差异完全隐藏成普通本地调用？

> [!answer]- 答案
> 远程调用存在高延迟、超时和部分失败；隐藏这些语义会让重试、幂等、一致性和容错设计产生错误假设。

---

> [!summary]- 模式总结（点击查看）
> | 维度 | 检查项 |
> |---|---|
> | 正确性 | 明确状态、原子性与异常路径 |
> | 性能 | 说明时间、空间、并发和 I/O 开销 |

## Related Notes

- [[28-操作系统学习地图]]
- [[30-操作系统高频易错点]]

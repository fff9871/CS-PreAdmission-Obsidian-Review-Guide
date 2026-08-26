---
source_pdf:
- 计算机考研复试面试常问问题 计算机网络篇.pdf
- 【精品】计算机保研面试_计算机网络常见题.pdf
- 专业课程基础概念复习.pdf
- 软院专业知识环节往届真题.pdf
- 6系2020年推免复试参考资料.pdf
part: 网络篇第12-14页；精品网络题第9页；基础概念第8页；软院真题第5页；6系资料第19-20页
keywords:
- computer-networks
- routing-protocols
- rip
- ospf
- bgp
---

# RIP、OSPF与BGP（★★★）

#computer-networks #network-layer #routing #routing-protocols #rip #ospf #bgp

## Overview Table

| 协议 | 范围/算法 | 度量与特点 |
|---|---|---|
| RIP | IGP，距离向量 | 跳数，最大有效 15 跳；周期交换路由，收敛较慢 |
| OSPF | IGP，链路状态 | 泛洪链路状态，构建拓扑后运行 Dijkstra；支持分区 |
| BGP | EGP，路径向量 | 在自治系统间传播前缀和 AS_PATH，重视策略与可达性 |

## 距离向量与链路状态

| 维度 | 距离向量 | 链路状态 |
|---|---|---|
| 掌握信息 | 到目的地的距离和下一跳 | 区域/网络拓扑图 |
| 交换对象 | 向邻居交换路由向量 | 泛洪本地链路状态 |
| 典型风险 | 路由环路、计数到无穷 | 状态库同步和计算开销 |

    RIP: 邻居间“听说”距离
    OSPF: 每台路由器获得拓扑 → SPF计算
    BGP: AS之间交换前缀 + 路径属性 + 策略

## IGP 与 EGP

IGP 在单个自治系统内部运行，优化内部收敛和代价；EGP 在自治系统之间运行，要考虑商业关系、安全、策略和规模。BGP 并不简单追求“最短跳数”。

> [!warning]
> OSPF 的链路状态泛洪不等于把完整路由表周期性广播给所有路由器；BGP 是应用层承载于 TCP 的路由协议，但其功能属于网络层控制平面。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| 跳数、15 跳 | RIP |
| 链路状态、Dijkstra、区域 | OSPF |
| 自治系统间、AS_PATH、策略 | BGP |

## Related Notes

- [[路由器、路由表与最长前缀匹配]]
- [[IP数据报、分片与转发]]
- [[练习-网络层与路由]]
- [[22-计算机网络高频易错点]]

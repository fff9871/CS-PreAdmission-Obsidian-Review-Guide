---
source_pdf:
- 计算机考研复试面试常问问题 计算机网络篇.pdf
- 专业课程基础概念复习.pdf
part: 网络篇第12-16页；基础概念第7-8页
keywords:
- computer-networks
- ip-datagram
- fragmentation
- forwarding
---

# IP数据报、分片与转发（★★★）

#computer-networks #network-layer #ipv4 #ip-datagram

## Overview Table

| 字段/机制 | 作用 |
|---|---|
| 版本、首部长度 | 解释首部格式 |
| 总长度 | 首部与数据总字节数 |
| 标识、DF、MF、片偏移 | IPv4 分片和重组 |
| TTL | 每经路由器递减，防止永久环路 |
| 协议 | 指示上交 TCP、UDP、ICMP 等 |
| 首部校验和 | 只校验 IPv4 首部 |
| 源/目的地址 | 端到端 IP 寻址 |

## 分片逻辑

当 IPv4 数据报大于下一跳 MTU 且 DF=0，路由器可分片；各片共享标识，片偏移以 8 字节为单位，除最后一片外 MF=1。重组通常只在目的主机进行。

    大IP数据报 > MTU
          ↓ 分片
      [片1 MF=1] [片2 MF=1] [末片 MF=0]
          └────────目的主机重组────────┘

## 转发流程

1. 检查首部并递减 TTL，必要时重算校验和。
2. 对目的 IP 查转发表，执行最长前缀匹配。
3. 确定下一跳和输出接口。
4. 通过 ARP 等机制获得下一跳链路地址，重新封装链路层帧。

> [!warning]
> 每一跳的链路层帧头会变化，源/目的 IP 通常保持端到端不变；NAT、隧道等机制是例外。IPv6 路由器不进行中途分片，需由源端配合路径 MTU 发现。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| TTL 归零 | 丢弃并通常返回 ICMP 超时报文 |
| 片偏移 | 以 8 字节为单位 |
| 每跳变化 | MAC 地址、TTL、首部校验和；普通转发中端到端 IP 不变 |

## Related Notes

- [[22-计算机网络高频易错点]]
- [[IPv4编址、子网与CIDR]]
- [[IP地址、MAC地址与ARP]]
- [[DHCP、ICMP与网络诊断]]
- [[练习-网络层与路由]]

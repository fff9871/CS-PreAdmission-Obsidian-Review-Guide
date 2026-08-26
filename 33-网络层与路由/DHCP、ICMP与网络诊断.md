---
source_pdf:
- 计算机考研复试面试常问问题 计算机网络篇.pdf
- 【精品】计算机保研面试_计算机网络常见题.pdf
- 专业课程基础概念复习.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
- 软院专业知识环节往届真题.pdf
part: 网络篇第15-16页；精品网络题第9-10页；基础概念第8页；精品综合题第12页；软院真题第5-6页
keywords:
- computer-networks
- dhcp
- icmp
- network-diagnostics
---

# DHCP、ICMP与网络诊断（★★★）

#computer-networks #network-layer #dhcp #icmp

## Overview Table

| 协议 | 主要用途 | 典型承载/特点 |
|---|---|---|
| DHCP | 动态分配 IP、掩码、网关、DNS 等配置 | 应用层协议，基于 UDP，初始阶段使用广播 |
| ICMP | 报告网络差错和提供诊断信息 | 封装在 IP 中，与 IP 协同工作 |
| ping | 测试可达性与 RTT | ICMP Echo Request/Reply |
| traceroute | 发现逐跳路径 | 利用 TTL 逐步增大和 ICMP 超时响应 |

## DHCP DORA

    客户端广播 Discover
           ↓
    服务器发送 Offer
           ↓
    客户端广播 Request
           ↓
    服务器发送 ACK

客户端选择一个 Offer 后广播 Request，也使未被选择的服务器知道结果。租约到期前通常会尝试续租。

## ICMP 常见类型

- 目的不可达：路由、端口或协议不可达等。
- 时间超过：TTL 归零或分片重组超时。
- 回送请求与回答：用于 ping。
- 重定向：提示主机使用更合适的下一跳。

> [!warning]
> ICMP 是控制与差错报告机制，不负责修复错误，也不会为“承载 ICMP 差错报文的数据报”再递归产生差错报文。防火墙可能过滤 ICMP，因此 ping 失败不必然代表应用服务不可用。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| 即插即用获取网络参数 | DHCP，DORA 四步 |
| TTL 逐步增加 | traceroute，利用 ICMP 时间超过 |
| ping | ICMP 回送请求/回答；不使用 TCP 端口 |

## Related Notes

- [[22-计算机网络高频易错点]]
- [[IPv4编址、子网与CIDR]]
- [[IP数据报、分片与转发]]
- [[DNS域名系统与解析]]
- [[浏览器输入URL后的完整过程]]
- [[练习-网络层与路由]]

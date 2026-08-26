---
source_pdf:
- 【精品】计算机保研面试_计算机网络常见题.pdf
- 专业课程基础概念复习.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
- 软院专业知识环节往届真题.pdf
- 6系2020年推免复试参考资料.pdf
part: 精品网络题第3-4页；基础概念第10-11页；精品综合题第12页；软院真题第5-6页；6系资料第19页
keywords:
- computer-networks
- url-lifecycle
- dns
- http
- tcp
---

# 浏览器输入URL后的完整过程（★★★）

#computer-networks #application-layer #url-lifecycle

## Overview Table

| 阶段 | 关键动作 | 典型协议/机制 |
|---|---|---|
| URL 解析 | 确定 scheme、主机、端口、路径 | 浏览器/应用逻辑 |
| 名称解析 | 域名得到 IP | DNS、缓存 |
| 寻找下一跳 | 判断同网或默认网关，获得 MAC | 路由表、ARP/NDP |
| 建立传输 | 创建可靠连接或 QUIC 会话 | TCP 三次握手 / QUIC |
| 安全握手 | 验证证书并协商密钥 | TLS |
| 应用请求 | 发送请求并接收响应 | HTTP |
| 渲染加载 | 解析 HTML、CSS、JS 并获取子资源 | 缓存、并发请求、渲染流水线 |

## 端到端流程

    URL
     ↓ 浏览器缓存/HSTS/代理判断
    DNS解析 → 目的IP
     ↓ 查本机路由，必要时ARP默认网关
    TCP握手 或 QUIC建连
     ↓ HTTPS则TLS握手
    HTTP请求 → 响应状态/首部/正文
     ↓
    解析、执行、布局、绘制，并继续加载子资源

## 分层回答法

- 应用层：DNS、HTTP、Cookie/缓存。
- 传输层：端口、TCP/UDP/QUIC、可靠与拥塞控制。
- 网络层：IP 路由、ICMP。
- 链路层：ARP/NDP、MAC 帧、交换机。
- 物理层：比特在介质上传输。

> [!warning]
> 实际过程会受 DNS/HTTP 缓存、连接复用、CDN、代理、IPv6、HTTP/2、HTTP/3 和服务工作线程影响。答题应先给稳定主线，再说明这些可能跳过或改变部分步骤。

## Exam/Test Patterns

| 追问 | 回答路径 |
|---|---|
| 域名如何变 IP | DNS 缓存→递归解析器→根/TLD/权威 |
| 跨网第一帧目的 MAC | 默认网关 MAC，不是服务器 MAC |
| HTTPS 多什么 | 在应用数据前完成 TLS 身份验证与密钥协商 |

## Related Notes

- [[DNS域名系统与解析]]
- [[HTTP请求、报文与状态管理]]
- [[HTTPS、TLS与证书]]
- [[TCP三次握手与连接建立]]
- [[IP地址、MAC地址与ARP]]
- [[练习-应用层协议与综合通信]]
- [[22-计算机网络高频易错点]]

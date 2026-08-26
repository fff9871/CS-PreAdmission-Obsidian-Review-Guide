---
source_pdf:
- 计算机考研复试面试常问问题 计算机网络篇.pdf
- 【精品】计算机保研面试_计算机网络常见题.pdf
- 专业课程基础概念复习.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
- 软院专业知识环节往届真题.pdf
part: 网络篇第22-23页；精品网络题第4页；基础概念第10-11页；精品综合题第12页；软院真题第5-6页
keywords:
- computer-networks
- http
- request-response
- cookies
---

# HTTP请求、报文与状态管理（★★★）

#computer-networks #application-layer #http

## Overview Table

| 主题 | 要点 |
|---|---|
| 模型 | 客户端请求、服务器响应 |
| 方法 | GET、POST、PUT、DELETE、HEAD 等 |
| 状态码 | 1xx 信息、2xx 成功、3xx 重定向、4xx 客户端错误、5xx 服务端错误 |
| 持久连接 | 多个请求复用连接，减少握手和慢启动开销 |
| 状态管理 | Cookie、Session、Token 在应用层补充状态 |
| 缓存 | Cache-Control、ETag、Last-Modified 等控制复用与验证 |

## 报文结构

    请求行 / 状态行
    Header: value
    Header: value
    空行
    可选消息体

HTTP/1.1 默认持久连接；HTTP/2 在一个连接中多路复用流并压缩首部；HTTP/3 基于 QUIC，在 UDP 之上提供加密和多路传输。

## 无状态与连接

HTTP 语义是无状态的：协议不要求服务器自动记住前一次请求。HTTP 可以使用持久 TCP/QUIC 连接，因此“无状态”不等于“每次都新建连接”。Cookie 或 Token 让服务器把多个请求关联到同一用户上下文。

> [!warning]
> GET 与 POST 的安全性不能只凭方法名判断；敏感数据必须通过 HTTPS 保护并做好授权、输入校验和 CSRF 等防护。GET 通常应是安全且幂等的，POST 通常不保证幂等。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| HTTP 是否有状态 | 协议语义无状态，应用可用 Cookie/Session/Token 维护状态 |
| 301/302/304 | 永久重定向、临时重定向/实现相关、缓存资源未修改 |
| HTTP/2 vs HTTP/1.1 | 二进制分帧、多路复用、首部压缩，但 TCP 丢包仍影响连接内流 |

## Related Notes

- [[22-计算机网络高频易错点]]
- [[HTTPS、TLS与证书]]
- [[DNS域名系统与解析]]
- [[浏览器输入URL后的完整过程]]
- [[练习-应用层协议与综合通信]]

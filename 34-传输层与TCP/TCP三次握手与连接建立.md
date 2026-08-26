---
source_pdf:
- 计算机考研复试面试常问问题 计算机网络篇.pdf
- 【精品】计算机保研面试_计算机网络常见题.pdf
- 专业课程基础概念复习.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
- 软院专业知识环节往届真题.pdf
part: 网络篇第18-20页；精品网络题第5-7页；基础概念第9页；精品综合题第8页；软院真题第4-6页
keywords:
- computer-networks
- tcp-handshake
- syn
- connection-establishment
---

# TCP三次握手与连接建立（★★★）

#computer-networks #transport-layer #tcp #tcp-handshake

## Overview Table

| 步骤 | 报文 | 状态意义 |
|---|---|---|
| 1 | 客户端 `SYN=1, seq=x` | 请求连接并声明初始序号 x |
| 2 | 服务器 `SYN=1, ACK=1, seq=y, ack=x+1` | 确认客户端并声明自己的初始序号 y |
| 3 | 客户端 `ACK=1, seq=x+1, ack=y+1` | 确认服务器，双方建立连接 |

## 时序图

    Client                              Server
      | ---- SYN, seq=x ----------------> |
      | <--- SYN+ACK, seq=y, ack=x+1 ---- |
      | ---- ACK, ack=y+1 --------------> |
      |          ESTABLISHED              |

## 为什么是三次

三次握手使双方都能确认：

1. 自己的发送能力和接收能力可用。
2. 对方的发送能力和接收能力可用。
3. 双方本次连接的初始序号得到确认。
4. 避免旧的延迟 SYN 让服务器长期误建连接。

服务器在收到最终 ACK 前通常处于 `SYN-RECEIVED`，半连接会占用一定资源，SYN flood 因此利用大量未完成握手消耗队列。

> [!warning]
> SYN 和 FIN 各占用一个序号，即使不携带应用数据。第三次握手可以携带数据；描述“客户端资源只在第三次握手后才分配”应视具体实现，不能当作协议硬性规则。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 为什么不能两次 | 服务器无法确认自己的 SYN 已被客户端接收，旧 SYN 也可能造成误连接 |
| 初始序号作用 | 区分字节流位置和旧连接报文 |
| SYN flood | 大量半连接耗尽资源，可用 SYN cookies 等缓解 |

## Related Notes

- [[TCP报文段、序号确认与可靠传输]]
- [[TCP四次挥手、半关闭与TIME-WAIT]]
- [[练习-传输层与TCP]]
- [[22-计算机网络高频易错点]]

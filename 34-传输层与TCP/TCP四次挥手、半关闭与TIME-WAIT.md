---
source_pdf:
- 计算机考研复试面试常问问题 计算机网络篇.pdf
- 【精品】计算机保研面试_计算机网络常见题.pdf
- 专业课程基础概念复习.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
- 软院专业知识环节往届真题.pdf
part: 网络篇第19-20页；精品网络题第6-7页；基础概念第10页；精品综合题第8页；软院真题第4页
keywords:
- computer-networks
- tcp-termination
- time-wait
- half-close
---

# TCP四次挥手、半关闭与TIME-WAIT（★★★）

#computer-networks #transport-layer #tcp #tcp-termination

## Overview Table

| 阶段 | 主动关闭方 | 被动关闭方 | 含义 |
|---|---|---|---|
| 1 | 发送 FIN | 收到 FIN | 主动方不再发送数据 |
| 2 | 收到 ACK | 发送 ACK | 被动方确认，连接进入半关闭 |
| 3 | 收到 FIN | 发送 FIN | 被动方也发送完毕 |
| 4 | 发送 ACK，进入 TIME-WAIT | 收到 ACK 后关闭 | 确认最终 FIN |

## 时序图

    Active close                         Passive close
      | ---- FIN ------------------------> |
      | <--- ACK ------------------------- |
      |       单向仍可传数据（半关闭）      |
      | <--- FIN ------------------------- |
      | ---- ACK ------------------------> |
      | TIME-WAIT 2MSL                    | CLOSED

## 为什么通常四次

TCP 是全双工连接。收到对方 FIN 只表示对方方向不再发送；本方可能还有数据，因此 ACK 与本方 FIN 通常分开发送。若本方也立即结束，ACK 和 FIN 可以合并，抓包未必总看到严格四个独立报文。

## TIME-WAIT 的作用

- 保证最终 ACK 丢失时，主动关闭方仍能重发 ACK。
- 让旧连接的延迟报文在网络中消失，避免污染相同四元组的新连接。

> [!warning]
> `2MSL` 是报文最大生存时间的两倍，不是 RTT。TIME-WAIT 通常由主动关闭方进入，但同时关闭等特殊情况会更复杂。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| 为什么四次 | 双向数据流独立关闭，ACK 与 FIN 可能分开 |
| 为什么等 2MSL | 可靠确认最后 FIN，并等待旧报文消失 |
| CLOSE-WAIT 多 | 应用收到 FIN 后迟迟未关闭本地套接字 |

## Related Notes

- [[TCP三次握手与连接建立]]
- [[TCP报文段、序号确认与可靠传输]]
- [[练习-传输层与TCP]]
- [[22-计算机网络高频易错点]]

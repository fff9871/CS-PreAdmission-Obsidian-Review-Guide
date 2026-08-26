---
source_pdf:
- 计算机考研复试面试常问问题 计算机网络篇.pdf
- 【精品】计算机保研面试_计算机网络常见题.pdf
- 专业课程基础概念复习.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
- 软院专业知识环节往届真题.pdf
- 6系2020年推免复试参考资料.pdf
part: 端口、UDP、TCP可靠传输、连接管理、流量与拥塞控制
keywords:
- practice
- computer-networks
- transport-layer
- tcp
---

# 传输层与TCP Practice（10 questions）

#practice #computer-networks #transport-layer #tcp

## Related Concepts

- [[传输层、端口、套接字与复用分用]]
- [[UDP协议与适用场景]]
- [[TCP报文段、序号确认与可靠传输]]
- [[TCP三次握手与连接建立]]
- [[TCP四次挥手、半关闭与TIME-WAIT]]
- [[TCP滑动窗口与流量控制]]
- [[TCP拥塞控制算法]]

> [!hint]- 核心模式（点击查看）
> | 关键词 | 回答路径 |
> |---|---|
> | TCP可靠 | 序号、ACK、定时器、重传、窗口 |
> | 建连与释放 | 双向能力、序号、半关闭、2MSL |
> | 两类控制 | rwnd保护接收端，cwnd保护网络 |

---

## Question 1 - 通信对象 [recall]
> 传输层提供哪两个对象之间的逻辑通信？

> [!answer]- 答案
> 不同主机上的应用进程之间。

---

## Question 2 - UDP特点 [recall]
> UDP 的三个主要特点是什么？

> [!answer]- 答案
> 无连接、面向报文、尽最大努力；首部小且无内建流量和拥塞控制。

---

## Question 3 - TCP可靠机制 [recall]
> TCP 依靠哪些机制实现可靠传输？

> [!answer]- 答案
> 校验和、序号、累计确认、定时器、重传、滑动窗口和拥塞控制。

---

## Question 4 - 三次握手 [recall]
> TCP 三次握手的三个标志组合是什么？

> [!answer]- 答案
> SYN；SYN+ACK；ACK。

---

## Question 5 - TIME-WAIT [recall]
> TIME-WAIT 等待 2MSL 的两个作用是什么？

> [!answer]- 答案
> 保证最后 ACK 可重传，并让旧连接延迟报文从网络中消失。

---

## Question 6 - 两种窗口 [recall]
> rwnd 与 cwnd 分别解决什么问题？

> [!answer]- 答案
> rwnd 反映接收方能力用于流量控制；cwnd 反映网络承载估计用于拥塞控制。

---

## Question 7 - 协议选型 [application]
> 实时语音允许少量丢包且重视时延，通常优先选择什么传输协议？

> [!answer]- 答案
> 通常优先 UDP，并由应用按需实现抖动缓冲、纠错或有限重传。

---

## Question 8 - 重复ACK [application]
> 发送方收到三个重复 ACK 时通常执行什么动作？

> [!answer]- 答案
> 触发快重传；经典 Reno 还会调整 ssthresh 并进入快恢复。

---

## Question 9 - 为何三次 [analysis]
> 两次握手为何不足以可靠建立 TCP 连接？

> [!answer]- 答案
> 服务器无法确认自己的 SYN 已被客户端接收，也难以排除网络中旧 SYN 导致的半开或误连接。

---

## Question 10 - 控制比较 [analysis]
> 接收窗口很大时，发送方为何仍不能无限提高发送速率？

> [!answer]- 答案
> 网络可能拥塞，发送还受 cwnd、路径容量、RTT、应用速度等限制；流量控制不等于拥塞控制。

---

> [!summary]- 模式总结（点击查看）
> | 类型 | 判断重点 |
> |---|---|
> | 可靠性 | 字节序号、累计确认与丢包恢复 |
> | 状态机 | 每个 FIN 只关闭一个方向 |
> | 性能 | 接收端窗口与网络拥塞窗口共同约束 |

## Related Notes

- [[20-计算机网络学习地图]]
- [[22-计算机网络高频易错点]]

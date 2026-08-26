---
source_pdf:
- 操作系统_第九章_分布式OS_wty.pdf
part: 分布式OS课件第1-42页
keywords:
- operating-systems
- distributed-systems
- rpc
- distributed-communication
---

# RPC、RMI与分布式通信（★★★）

#operating-systems #distributed-systems #rpc #distributed-communication

## Overview Table

| 机制 | 抽象 | 关键点 |
|---|---|---|
| 消息传递 | 显式 send/receive | 编址、缓冲、可靠性 |
| RPC | 像调用本地过程 | stub、序列化、绑定、超时 |
| RMI | 调用远程对象方法 | 对象引用、接口、生命周期 |
| 发布订阅 | 按主题异步分发 | 解耦、顺序、重复和积压 |

## RPC 路径

    client → client stub → marshal → network
       ← result/unmarshal ← server stub ← server procedure

网络故障使调用结果可能出现：未执行、执行一次、执行多次、已执行但回复丢失。系统常提供至多一次、至少一次等语义，而“恰好一次”通常需持久化去重与事务边界。

## 幂等与重试

读取和设值型操作较易设计为幂等；“余额加 10”重试会重复生效，应使用请求 ID、去重表或条件更新。

> [!warning]
> RPC 只是外观像本地调用：参数复制、部分失败、版本兼容、时延和安全边界完全不同。超时不能证明服务端未执行。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| Stub | 封装参数编解码和通信 |
| At-least-once | 可能重复，要求幂等/去重 |
| Timeout | 结果未知，不等于未执行 |

## Related Notes

- [[分布式系统目标、透明性与体系结构]]
- [[分布式文件系统、一致性与容错]]
- [[进程间通信：管道、消息、共享内存与Socket]]
- [[练习-安全虚拟化与分布式OS]]
- [[30-操作系统高频易错点]]

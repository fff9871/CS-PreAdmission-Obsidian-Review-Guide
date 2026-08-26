---
source_pdf:
- 操作系统_第5章_IO_wty_2021.pdf
- 计算考研复试面试常问问题 操作系统篇.pdf
part: I/O课件第1-87页；操作系统篇第15-17页
keywords:
- operating-systems
- io-management
- async-io
- io-multiplexing
---

# 阻塞非阻塞、同步异步与I-O多路复用（★★★）

#operating-systems #io-management #async-io #io-multiplexing

## Overview Table

| 维度 | 选项 | 判断问题 |
|---|---|---|
| 阻塞/非阻塞 | 无数据时调用者是否睡眠 | 调用能否立即返回 |
| 同步/异步 | 完成数据传输由谁等待/获知 | 返回时操作是否已完成 |
| 多路复用 | 一次等待多个描述符的就绪事件 | select/poll/epoll 等 |

## 常见组合

| 模式 | 行为 |
|---|---|
| 阻塞同步 I/O | 调用者睡眠，数据就绪并复制后返回 |
| 非阻塞同步 I/O | 未就绪立即报 EAGAIN，调用者稍后重试 |
| 就绪通知 + 同步读写 | 多路复用通知可读，再调用 read 完成数据获取 |
| 异步 I/O | 提交请求后继续执行，内核完成后通知结果 |

    descriptors → wait readiness → ready set
                                  ↓
                             perform I/O

水平触发持续报告“仍就绪”的对象；边缘触发主要报告状态变化，通常需循环读写直至 EAGAIN。

> [!warning]
> 非阻塞不等于异步，epoll 就绪通知也不等于数据已经全部处理完成。文件、管道、Socket 和不同 OS 的异步语义可能不同。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| O_NONBLOCK | 未就绪时立即返回 |
| select/poll/epoll | 等待多个 fd 的就绪性 |
| 真异步 I/O | 内核完成操作后通知调用者 |

## Related Notes

- [[I-O软件层次、驱动与设备控制器]]
- [[文件、目录、inode与文件描述符]]
- [[进程间通信：管道、消息、共享内存与Socket]]
- [[练习-文件系统、磁盘与I-O]]
- [[30-操作系统高频易错点]]

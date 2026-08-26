---
source_pdf:
- 操作系统_第7章_文件系统_wty_2021.pdf
- 计算考研复试面试常问问题 操作系统篇.pdf
- 指导书.pdf
part: 文件系统课件第1-156页；操作系统篇第14-16页；实验指导书第180-197页
keywords:
- operating-systems
- file-system
- inode
- file-descriptor
---

# 文件、目录、inode与文件描述符（★★★）

#operating-systems #file-system #inode #file-descriptor

## Overview Table

| 对象 | 保存内容 |
|---|---|
| 目录项 | 文件名到 inode/文件标识的映射 |
| inode/FCB | 类型、权限、所有者、大小、时间、数据块指针 |
| 系统打开文件表 | 当前偏移、状态标志、引用计数等 |
| 进程 fd 表 | 小整数 fd 到打开文件对象的引用 |

## 路径到数据

    pathname
      → 逐级目录查找
      → inode/FCB
      → 权限检查
      → open file object
      → fd in process
      → data blocks

`dup` 或 fork 后多个 fd 可引用同一打开文件对象并共享偏移；分别 open 同一路径通常产生不同打开对象和偏移。

## 链接

硬链接创建另一目录项指向同一 inode，删除名字只减少链接计数；符号链接是保存目标路径的独立文件，可跨文件系统但可能悬空。

> [!warning]
> 文件名通常不存于 inode，而在目录项中；打开文件仍被引用时，即使最后一个目录名被删除，数据也可继续存在直到引用释放。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| fd 是什么 | 进程 fd 表中的索引 |
| inode 是否存文件名 | 通常不存，文件名位于目录项 |
| 硬链接 vs 符号链接 | 同 inode 的目录项 vs 保存路径的独立文件 |

## Related Notes

- [[连续、链接、索引分配与空闲空间管理]]
- [[文件系统挂载、一致性与日志]]
- [[BUAA-MOS文件系统、管道与Shell]]
- [[练习-文件系统、磁盘与I-O]]
- [[30-操作系统高频易错点]]

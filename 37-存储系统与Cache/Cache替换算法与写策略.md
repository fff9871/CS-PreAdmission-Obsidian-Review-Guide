---
source_pdf:
- 计算机考研复试面试常问问题 计算机组成原理篇.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
- 6系2020年推免复试参考资料.pdf
part: 组成原理篇第9-10页；精品综合题第29-30页；6系资料第18页
keywords:
- computer-organization
- cache-replacement
- cache-write-policy
- lru
---

# Cache替换算法与写策略（★★★）

#computer-organization #memory-hierarchy #cache #cache-replacement #cache-write-policy

## Overview Table

| 维度 | 策略 | 特点 |
|---|---|---|
| 替换 | Random | 硬件简单，结果随机 |
| 替换 | FIFO | 淘汰最早进入者，不反映近期使用 |
| 替换 | LRU/近似 LRU | 淘汰最久未用者，利用时间局部性 |
| 写命中 | Write-through | 同时写 Cache 和下层，简单但流量大 |
| 写命中 | Write-back | 只写 Cache，置脏位，替换时写回 |
| 写缺失 | Write-allocate | 先把块调入再写，常配 write-back |
| 写缺失 | No-write-allocate | 直接写下层，常配 write-through |

## 写路径

    CPU写命中
      ├─ Write-through → Cache + 下层（常配写缓冲）
      └─ Write-back    → 只改Cache并置Dirty

    替换脏行 → 先写回下层 → 再装入新块

## 替换算法边界

直接映射每个主存块只有唯一位置，无需在多路之间选择替换对象；替换算法主要用于组相联和全相联。真实处理器常采用伪 LRU 以降低精确维护代价。

> [!warning]
> “写回一定更快”并不绝对：它减少下层写流量，但需要脏位和复杂一致性处理；多核系统还要配合缓存一致性协议。

## Exam/Test Patterns

| 场景 | 回答 |
|---|---|
| 写直达 | 每次命中都更新下层，常需写缓冲 |
| 写回 | 命中只改 Cache，脏块替换时写下层 |
| 直接映射替换 | 无选择，目标行由地址决定 |

## Related Notes

- [[26-计算机组成高频易错点]]
- [[Cache结构、命中率与平均访问时间]]
- [[Cache映射方式]]
- [[虚拟存储、页表与TLB]]
- [[练习-存储系统与Cache]]

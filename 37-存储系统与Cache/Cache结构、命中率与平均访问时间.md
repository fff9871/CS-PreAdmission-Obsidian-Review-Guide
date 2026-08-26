---
source_pdf:
- 计算机考研复试面试常问问题 计算机组成原理篇.pdf
- 【精品】计算机保研面试专业课常见问题.pdf
- 6系2020年推免复试参考资料.pdf
part: 组成原理篇第7-10页；精品综合题第29-30页；6系资料第18页
keywords:
- computer-organization
- cache
- cache-addressing
- amat
---

# Cache结构、命中率与平均访问时间（★★★）

#computer-organization #memory-hierarchy #cache #cache-addressing

## Overview Table

| 概念 | 含义 |
|---|---|
| Cache 行/块 | Cache 与主存交换的基本单位 |
| Tag | 判断当前行保存哪个主存块 |
| Index/组索引 | 选择 Cache 行或组 |
| Block Offset | 选择块内字节/字 |
| 命中率 h | 访问在 Cache 中找到的比例 |
| 缺失代价 | 未命中后从下层取块并恢复执行的额外时间 |

## 地址划分

    CPU地址 = [ Tag | Set Index | Block Offset ]
                         ↓             ↓
                      选择组       选择块内字节
                Tag比较 + Valid → 命中/缺失

若块大小为 `2^b` 字节，则块内偏移 b 位；若有 `2^s` 个组，则组索引 s 位，其余高位通常作为 Tag。

## 平均访存时间 AMAT

单级 Cache 常用：

`AMAT = 命中时间 + 缺失率 × 缺失代价`

多级 Cache 可递归展开：L1 缺失代价包含访问 L2 的平均时间。

> [!warning]
> 命中率高不一定 AMAT 更低：提高相联度或块大小可能增加命中时间。缺失代价也应区分是否包含再次访问 Cache、写回脏块和多级存储开销。

## Exam/Test Patterns

| 场景 | 回答 |
|---|---|
| 求地址字段 | 先由块大小求 offset，再由组数求 index，其余为 tag |
| 求 AMAT | 命中时间加缺失率乘缺失代价 |
| Cache 作用 | 利用局部性缓解 CPU 与主存速度差 |

## Related Notes

- [[26-计算机组成高频易错点]]
- [[Cache映射方式]]
- [[Cache替换算法与写策略]]
- [[存储层次与局部性]]
- [[练习-存储系统与Cache]]

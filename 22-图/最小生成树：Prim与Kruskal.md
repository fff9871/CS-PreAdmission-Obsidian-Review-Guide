---
source_pdf:
  - "计算机考研复试面试常问问题 数据结构篇.pdf"
  - "【精品】计算机保研面试_数据结构常见题.pdf"
  - "6系2020年推免复试参考资料.pdf"
  - "【精品】计算机保研面试专业课常见问题.pdf"
part: "图：数据结构篇第15-16页；常见题第15-16页；6系第17页；专业课第5页"
keywords: [data-structures, graphs, minimum-spanning-tree, greedy]
---


# 最小生成树：Prim与Kruskal（★★★）

#data-structures #graphs #minimum-spanning-tree

## Overview Table

| 算法 | 贪心对象 | 核心结构 | 更适合 |
|---|---|---|---|
| Prim | 从已选顶点集向外选最轻边 | 最小距离数组/小根堆 | 稠密图（矩阵版） |
| Kruskal | 按权从小到大选不造成环的边 | 排序+并查集 | 稀疏图 |

## 目标与性质

最小生成树（MST）仅对 **连通无向带权图** 定义：选择 $V-1$ 条边连通全部顶点，使总权值最小。权值不同时 MST 唯一；权值重复时也可能仍唯一，但不能仅凭重复就断定不唯一。

```text
Prim:    顶点集不断长大
Kruskal: 森林通过安全边不断合并
```

## 复杂度

- Prim 邻接矩阵：$O(V^2)$。
- Prim 邻接表+二叉堆：$O(E\log V)$。
- Kruskal：排序主导，$O(E\log E)$，并查集操作近似常数。

> [!warning]
> MST 最小化的是整棵树的边权总和，不保证某个源点到各顶点的路径最短。

## Exam/Test Patterns

| 提问 | 回答 |
|---|---|
| Kruskal 如何判环 | 若两端点已在同一并查集，加边会成环 |
| 非连通图 | 得到最小生成森林，不是一棵生成树 |
| Prim 与 Dijkstra | 都逐步扩展，但 Prim 维护连到树的最小边，Dijkstra 维护到源点的最短路 |

## Related Notes

- [[堆、Huffman树与并查集]]
- [[最短路：Dijkstra、Bellman-Ford与Floyd]]
- [[练习-图]]
- [[14-数据结构高频易错点]]

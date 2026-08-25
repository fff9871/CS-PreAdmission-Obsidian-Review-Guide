---
source_pdf:
  - "计算机考研复试面试常问问题 数据结构篇.pdf"
  - "【精品】计算机保研面试_数据结构常见题.pdf"
  - "王道机试指南.pdf"
  - "6系2020年推免复试参考资料.pdf"
part: "图：数据结构篇第15-16页；常见题第16页；王道第136-149页；6系第17页"
keywords: [data-structures, graphs, shortest-path, dijkstra]
---


# 最短路：Dijkstra、Bellman-Ford与Floyd（★★★）

#data-structures #graphs #shortest-path

## Overview Table

| 算法 | 问题 | 负权边 | 负环 | 典型复杂度 |
|---|---|---|---|---:|
| BFS | 无权单源 | 不适用 | 不适用 | $O(V+E)$ |
| Dijkstra | 非负权单源 | 不允许 | 不允许 | 堆优化 $O((V+E)\log V)$ |
| Bellman-Ford | 可含负边的单源 | 允许 | 可检测可达负环 | $O(VE)$ |
| Floyd-Warshall | 全源最短路 | 允许 | 可用 $d[i][i]<0$ 检测 | $O(V^3)$ |

## Dijkstra 松弛

```text
dist[s]=0，其余=∞
反复取未确定且 dist 最小的 u
  对边 (u,v,w): dist[v] = min(dist[v], dist[u]+w)
```

非负权保证了当 $u$ 被选中时，其最短距离已无法再被未选顶点改善。

## Floyd 状态转移

$$d_{ij}^{(k)}=\min\left(d_{ij}^{(k-1)},d_{ik}^{(k-1)}+d_{kj}^{(k-1)}\right)$$

三层循环中 $k$ 必须在最外层，表示逐步允许新的中间顶点。

> [!warning]
> Dijkstra 不是“不能有负环”，而是只要存在可达负权边，其贪心确定顶点的逻辑就可能失效。

## Exam/Test Patterns

| 场景 | 选择 |
|---|---|
| 无权图单源 | BFS |
| 稀疏非负权图单源 | 堆优化 Dijkstra |
| 有负边且需检负环 | Bellman-Ford |
| 顶点较少的全源路径 | Floyd-Warshall |

## Related Notes

- [[DFS、BFS与图遍历]]
- [[最小生成树：Prim与Kruskal]]
- [[练习-图]]
- [[14-数据结构高频易错点]]

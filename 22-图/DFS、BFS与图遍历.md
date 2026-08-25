---
source_pdf:
  - "计算机考研复试面试常问问题 数据结构篇.pdf"
  - "【精品】计算机保研面试_数据结构常见题.pdf"
  - "王道机试指南.pdf"
  - "软院专业知识环节往届真题.pdf"
part: "图遍历：数据结构篇第15页；常见题第14页；王道第157-184页；软院真题第1页"
keywords: [data-structures, graphs, dfs, bfs]
---


# DFS、BFS与图遍历（★★★）

#data-structures #graphs #graph-traversal

## Overview Table

| 维度 | DFS | BFS |
|---|---|---|
| 控制结构 | 递归或栈 | 队列 |
| 策略 | 深入后回溯 | 按距离分层扩展 |
| 无权最短路 | 不保证 | 保证最少边数 |
| 典型应用 | 连通性、环、拓扑/强连通 | 层序、无权最短路 |

## 通用框架

```text
DFS(u):                BFS(s):
  mark u                 mark s, enqueue s
  for v in adj[u]:       while queue not empty:
    if unmarked v:         u = dequeue
      DFS(v)                for v in adj[u]:
                               if unmarked v: mark + enqueue
```

用邻接表时，两者时间复杂度均为 $O(V+E)$；邻接矩阵为 $O(V^2)$。非连通图需对每个未访问顶点重新启动遍历，得到遍历森林。

> [!warning]
> 必须在“入队时”标记 BFS 结点；若到出队才标记，同一顶点可被多次入队。递归 DFS 还需防止深度过大导致栈溢出。

## Exam/Test Patterns

| 场景 | 选择 |
|---|---|
| 无权图最少步数 | BFS，首次到达即是最短层数 |
| 判断是否存在一条路 | DFS/BFS 均可 |
| 需要恢复路径 | 记录 `parent` 或前驱状态 |

## Related Notes

- [[图的概念与存储]]
- [[队列、双端队列与循环队列]]
- [[拓扑排序与关键路径]]
- [[练习-图]]
- [[14-数据结构高频易错点]]

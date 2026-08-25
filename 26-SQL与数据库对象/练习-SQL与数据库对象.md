---
source_pdf:
  - "数据库复习.pdf"
  - "专业课程基础概念复习.pdf"
  - "【精品】计算机保研面试专业课常见问题.pdf"
  - "软院专业知识环节往届真题.pdf"
part: "SQL分类、查询、连接与数据库对象"
keywords: [practice, sql]
---

# SQL与数据库对象 Practice（10 questions）

#practice #database #sql

## Related Concepts

- [[SQL语言分类与数据定义]]
- [[单表查询、聚合与分组]]
- [[多表连接、子查询与集合运算]]
- [[视图、存储过程与触发器]]

> [!hint]- 核心模式（点击查看）
> | 关键词 | 回答路径 |
> |---|---|
> | 聚合前过滤 | WHERE |
> | 聚合后过滤 | HAVING |
> | 保留左表行 | LEFT JOIN 条件谨慎放 ON |

## Question 1 - SQL 分类 [recall]
> DDL、DML、DCL、TCL 各负责什么？

> [!answer]- 答案
> 分别负责对象定义、数据增删改、权限控制和事务控制；SELECT 常单列为 DQL。

---

## Question 2 - 执行顺序 [recall]
> FROM、WHERE、GROUP BY、HAVING、SELECT 的逻辑顺序是什么？

> [!answer]- 答案
> FROM/连接、WHERE、GROUP BY、HAVING、SELECT。

---

## Question 3 - COUNT [recall]
> COUNT(*) 与 COUNT(col) 有何区别？

> [!answer]- 答案
> 前者统计结果行；后者忽略 col 为 NULL 的行。

---

## Question 4 - 集合运算 [recall]
> UNION 与 UNION ALL 的区别是什么？

> [!answer]- 答案
> UNION 合并后去重；UNION ALL 保留重复，通常代价更低。

---

## Question 5 - 视图 [recall]
> 普通视图与物化视图有何区别？

> [!answer]- 答案
> 普通视图主要保存查询定义；物化视图保存结果并需要刷新。

---

## Question 6 - 触发器 [recall]
> 触发器与存储过程的调用方式有何区别？

> [!answer]- 答案
> 存储过程被显式调用；触发器由指定的数据或数据库事件自动触发。

---

## Question 7 - 外连接 [application]
> LEFT JOIN 后要筛选右表状态但仍保留未匹配左表行，条件宜放哪里？

> [!answer]- 答案
> 通常放在 ON 中；若放 WHERE，右表为 NULL 的行会被过滤，可能退化为内连接。

---

## Question 8 - NOT IN [application]
> 子查询可能返回 NULL 时，为何 NOT EXISTS 往往比 NOT IN 稳妥？

> [!answer]- 答案
> NOT IN 遇到 NULL 会受三值逻辑影响而产生 UNKNOWN；NOT EXISTS 可用明确关联条件表达反连接。

---

## Question 9 - N+1 [analysis]
> 循环中逐行发查询为什么慢，如何改？

> [!answer]- 答案
> 它增加大量网络往返与重复执行开销；应使用连接、批量 IN、预取或批处理合并查询。

---

## Question 10 - 触发器取舍 [analysis]
> 为什么关键规则不应一律写成触发器？

> [!answer]- 答案
> 触发器隐式执行、顺序和递归难排查；能用声明式约束表达时通常更清晰、可验证。

---

> [!summary]- 模式总结（点击查看）
> | 维度 | 检查项 |
> |---|---|
> | 定义 | 先给准确边界，再给例子 |
> | 机制 | 说明目标、步骤、代价和例外 |
> | 选型 | 结合一致性、性能、维护与工作负载 |

## Related Notes

- [[16-数据库学习地图]]
- [[18-数据库高频易错点]]

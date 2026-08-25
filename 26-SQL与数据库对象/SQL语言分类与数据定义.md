---
source_pdf:
  - "数据库复习.pdf"
  - "专业课程基础概念复习.pdf"
  - "软院专业知识环节往届真题.pdf"
  - "【精品】计算机保研面试专业课常见问题.pdf"
part: "数据库复习第1页；基础概念第15页；软院真题第8页；专业课第31-33页"
keywords: [database, sql, ddl]
---

# SQL语言分类与数据定义（★★★）

#database #sql #ddl

## Overview Table

| 项目 | 要点 |
|---|---|
| DDL | 定义模式对象：CREATE、ALTER、DROP |
| DML | 插入、更新、删除：INSERT、UPDATE、DELETE |
| DQL | 查询：SELECT |
| DCL | 权限控制：GRANT、REVOKE |
| TCL | 事务控制：COMMIT、ROLLBACK、SAVEPOINT |

## 建表要点

列需声明数据类型、NULL 规则、默认值，以及主键、唯一、检查和外键约束。

## 约束位置

列级约束适合单列；表级约束可表达组合主键、组合唯一和多列检查。

## 删除语义

DELETE 删除行且可带 WHERE；TRUNCATE 通常快速清空表；DROP 删除对象定义。具体事务性和日志行为依数据库产品而异。

> [!warning]
> SQL 分类在不同教材中略有差异，例如 SELECT 可归入 DQL，也可视为广义 DML。面试时说明采用的分类即可。

## Exam/Test Patterns

| 场景/关键词 | 回答 |
|---|---|
| DDL/DML/DCL/TCL | 按定义、数据操作、权限、事务控制分类 |
| 外键 | 引用目标应是候选键或唯一键，并指定更新删除动作 |
| DROP/TRUNCATE/DELETE | 对象定义、整表数据、按条件删除，语义和事务行为不同 |

## Related Notes

- [[关系模型、键与完整性约束]]
- [[单表查询、聚合与分组]]
- [[视图、存储过程与触发器]]
- [[练习-SQL与数据库对象]]
- [[18-数据库高频易错点]]

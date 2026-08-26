---
source_pdf:
- 操作系统_第八章_安全_wty.pdf
part: 安全课件第1-66页
keywords:
- operating-systems
- system-security
- access-control
- capabilities
---

# DAC、MAC、RBAC与能力表（★★★）

#operating-systems #system-security #access-control #capabilities

## Overview Table

| 模型 | 决策依据 | 特点 |
|---|---|---|
| DAC | 对象所有者决定授权 | 灵活，权限可传播 |
| MAC | 主体许可级与对象标签、强制策略 | 用户不能任意改变，适合高保证系统 |
| RBAC | 用户—角色—权限 | 便于组织管理和职责分离 |
| ABAC | 主体/对象/环境属性 | 表达细粒度上下文策略 |
| Capability | 主体持有不可伪造的对象权限令牌 | 便于委托，需控制传播与撤销 |

## 访问矩阵两种实现

    rows(subjects) × columns(objects) = rights

- ACL：按对象列出哪些主体拥有哪些权限。
- Capability list：按主体列出能访问哪些对象及权限。

Unix 模式位和 ACL 更接近对象侧控制；文件描述符常表现为进程持有的能力式句柄。

## 策略原则

RBAC 可设计互斥角色实现职责分离；MAC 经典模型常用 Bell-LaPadula 保密性或 Biba 完整性规则；能力系统需防伪造并设计撤销/衰减。

> [!warning]
> ACL 和 capability 是访问矩阵的不同组织方式，不等于完整安全策略；root/管理员能力也应受审计和最小化控制。

## Exam/Test Patterns

| 需求 | 模型 |
|---|---|
| 资源所有者自主授权 | DAC |
| 安全标签强制流动 | MAC |
| 按岗位批量授权 | RBAC |
| 持有令牌即可访问 | Capability |

## Related Notes

- [[身份认证、授权与访问控制]]
- [[安全威胁、恶意软件与系统加固]]
- [[文件、目录、inode与文件描述符]]
- [[练习-安全虚拟化与分布式OS]]
- [[30-操作系统高频易错点]]

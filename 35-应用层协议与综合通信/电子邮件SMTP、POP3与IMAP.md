---
source_pdf:
- 计算机考研复试面试常问问题 计算机网络篇.pdf
- 专业课程基础概念复习.pdf
part: 网络篇第23页；基础概念第10-11页
keywords:
- computer-networks
- email-protocols
- smtp
- pop3
- imap
---

# 电子邮件SMTP、POP3与IMAP（★★★）

#computer-networks #application-layer #email-protocols #smtp #pop3 #imap

## Overview Table

| 协议 | 方向/用途 | 常见特点 |
|---|---|---|
| SMTP | 客户端提交邮件、邮件服务器之间转发 | 推送式，基于 TCP；常见端口 25/587/465 |
| POP3 | 用户从服务器取信 | 模型简单，传统上偏下载到本地；TCP 110/995 |
| IMAP | 用户远程管理服务器邮箱 | 保留文件夹、状态和多设备同步；TCP 143/993 |
| MIME | 扩展邮件正文和附件格式 | 支持非 ASCII、附件和多媒体内容 |

## 邮件传输链

    发件人MUA --SMTP提交--> 发件服务器
       发件服务器 --DNS查MX-->
       发件服务器 --SMTP转发--> 收件服务器
       收件人MUA <--IMAP/POP3-- 收件服务器

SMTP 负责“发送/转发”，POP3 和 IMAP 负责“访问邮箱”。现代 Webmail 的浏览器前端使用 HTTP/HTTPS，但服务端之间仍常用 SMTP。

## POP3 与 IMAP

| 维度 | POP3 | IMAP |
|---|---|---|
| 邮件状态 | 偏本地下载 | 服务器保存并同步 |
| 多设备 | 能力较弱 | 更适合多设备一致视图 |
| 文件夹/搜索 | 较简单 | 支持远程文件夹和状态管理 |

> [!warning]
> 端口号和加密方式受部署配置影响；“SMTP 只能用 25”并不准确。邮件内容安全还依赖 TLS、身份认证、反垃圾与 DKIM/SPF/DMARC 等机制。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| 发邮件 | SMTP |
| 多设备同步邮箱 | IMAP |
| 简单下载取信 | POP3 |

## Related Notes

- [[22-计算机网络高频易错点]]
- [[DNS域名系统与解析]]
- [[HTTPS、TLS与证书]]
- [[FTP控制连接与数据连接]]
- [[练习-应用层协议与综合通信]]

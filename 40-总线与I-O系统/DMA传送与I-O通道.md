---
source_pdf:
- 计算机考研复试面试常问问题 计算机组成原理篇.pdf
- 专业课程基础概念复习.pdf
- 计算考研复试面试常问问题 操作系统篇.pdf
- 6系2020年推免复试参考资料.pdf
part: 组成原理篇第16页；基础概念第1、5页；操作系统篇第16-17页；6系资料第18页
keywords:
- computer-organization
- dma
- channel-io
- direct-memory-access
---

# DMA传送与I-O通道（★★★）

#computer-organization #io-system #dma #channel-io

## Overview Table

| 方式 | CPU 干预粒度 | 控制者 |
|---|---|---|
| 中断驱动 | 常按字/少量数据中断 | CPU 服务程序 |
| DMA | CPU 配置一次，DMA 控制器传一个数据块 | DMA 控制器 |
| I/O 通道 | CPU 给出通道程序，可管理一组复杂 I/O | 专用 I/O 处理器 |

## DMA 流程

1. CPU 设置源/目的地址、方向、长度并启动 DMA。
2. DMA 请求并获得总线控制权。
3. 设备与主存直接传送，DMA 更新地址和计数。
4. 数据块完成或出错后，DMA 中断 CPU。

    CPU --配置--> DMA Controller
                     ↕ 总线仲裁
    Device <======> Memory
             块传送
    DMA --完成中断--> CPU

## DMA 占用总线

- 停止 CPU 访存：DMA 连续占用，传输快但 CPU 等待。
- 周期挪用：DMA 在若干存储周期中穿插传输。
- 透明 DMA：利用 CPU 不访问总线的周期，控制复杂。

> [!warning]
> DMA 减少 CPU 搬运开销，但不等于零开销。CPU 仍需配置、处理中断和驱动逻辑；现代系统还要处理虚拟地址映射、IOMMU 与 Cache 一致性。

## Exam/Test Patterns

| 关键词 | 回答 |
|---|---|
| 设备与主存直接块传输 | DMA |
| DMA 是否完全绕过 CPU | 数据阶段大多绕过，初始化和完成处理仍需 CPU |
| 通道 vs DMA | 通道可执行 I/O 程序并控制多设备，自治程度更高 |

## Related Notes

- [[26-计算机组成高频易错点]]
- [[总线仲裁与主设备选择]]
- [[程序查询与中断驱动I-O]]
- [[中断响应、优先级与向量]]
- [[练习-总线与I-O系统]]

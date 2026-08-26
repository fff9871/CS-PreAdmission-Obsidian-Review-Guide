---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第13-14页训练ResNet示例的数据流程扩展
keywords:
- machine-learning
- pytorch
- dataloader
- data-pipeline
---

# Dataset、DataLoader、Batch与Shuffle（★★★）

#machine-learning #pytorch #dataloader #data-pipeline

## Overview Table

| 组件 | 作用 |
|---|---|
| Dataset | 定义样本数与按索引取样 |
| DataLoader | 批处理、打乱、多进程加载和拼接 |
| Sampler | 决定索引顺序/采样权重 |
| collate_fn | 把样本列表组装成batch |

## 训练数据路径

    files/records
      → Dataset.__getitem__ + train transform
      → Sampler/shuffle
      → worker processes
      → collate batch
      → device transfer

训练集通常 shuffle，验证/测试保持确定顺序；分布式训练使用 DistributedSampler，并在每个 epoch 设置 epoch 以改变随机顺序。

## 性能参数

`num_workers`、`pin_memory`、prefetch、persistent workers 与异步 device copy 可提高吞吐，但最佳值依磁盘、CPU、增强和GPU速度。

> [!warning]
> 多进程 DataLoader 的随机种子、文件句柄和不可序列化对象需正确处理；对时间序列和有序任务不能随意 shuffle。

## Exam/Test Patterns

| 问法 | 回答 |
|---|---|
| shuffle训练集 | 减少固定顺序偏差、形成随机mini-batch |
| collate_fn | 处理变长样本、自定义batch组装 |
| pin_memory | 加速CPU pinned memory到CUDA传输 |

## Related Notes

- [[数据预处理、标准化与特征工程]]
- [[PyTorch训练循环、Loss与Optimizer]]
- [[训练集、验证集、测试集与交叉验证]]
- [[练习-PyTorch与训练实践]]
- [[34-机器学习高频易错点]]

---
source_pdf:
- 【精品】计算机保研面试_机器学习常见题.pdf
part: 第1-14页分类与训练实践主题的评估扩展
keywords:
- machine-learning
- ml-fundamentals
- classification-metrics
- roc-auc
---

# 分类指标、ROC-AUC与阈值（★★★）

#machine-learning #ml-fundamentals #classification-metrics #roc-auc

## Overview Table

| 指标 | 公式 | 关注 |
|---|---|---|
| Accuracy | `(TP+TN)/N` | 总体正确率 |
| Precision | `TP/(TP+FP)` | 预测为正中有多少为真 |
| Recall/TPR | `TP/(TP+FN)` | 真正例中找回多少 |
| Specificity | `TN/(TN+FP)` | 真负例识别能力 |
| F1 | `2PR/(P+R)` | Precision 与 Recall 调和平均 |
| ROC-AUC | TPR 对 FPR 曲线面积 | 跨阈值排序能力 |
| PR-AUC | Precision 对 Recall 曲线面积 | 正类稀少时更直观 |

## 阈值与成本

    predicted score → threshold τ → class
                         ↓
                 precision/recall tradeoff

阈值应依据误报与漏报成本、资源容量和概率校准选择，而不是默认固定 0.5。多分类要说明 micro、macro 或 weighted 平均。

> [!warning]
> 类别极不平衡时 Accuracy 可能虚高；AUC 衡量排序而非某个部署阈值的实际收益，概率校准也不由 AUC 保证。

## Exam/Test Patterns

| 业务 | 优先指标 |
|---|---|
| 疾病筛查怕漏诊 | Recall |
| 告警处理成本高 | Precision |
| 极不平衡排序 | PR-AUC + 阈值指标 |

## Related Notes

- [[回归、分类与排序任务]]
- [[数据泄漏、类别不平衡与分布偏移]]
- [[逻辑回归、Sigmoid与交叉熵]]
- [[练习-机器学习基础与评估]]
- [[34-机器学习高频易错点]]

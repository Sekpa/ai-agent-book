# 评估系统是否真的用好了记忆

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

记忆系统可能保存了正确事实，却在需要时找不到；也可能找到片段，却误解了指代。本实验把记忆评估分层，让你定位失败发生在保存、检索还是综合使用阶段。

## 理解实验

直接召回检查显式事实，语境推理检查跨轮关联，跨会话综合检查多段信息的联合使用。关键词指标便于快速检查，但无法完整判断语义正确性，因此它与模型裁判应被看作不同工具。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行离线关键词对照，选一个得分高和一个得分低的回答，人工核对它们是否真正满足问题。理解指标边界后，再按技术参考配置模型裁判，比较两种评分是否一致。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py --mode compare --metric keyword-recall
```

## 怎样解释结果

包含关键词不等于回答正确；改写成同义表达也可能被关键词规则漏掉。查看单题结果比只看平均分更容易找到这类偏差。

## 继续思考

一个回答记住了旧地址却漏掉了用户后来搬家，应该在哪一层被发现？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[main.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/user-memory-evaluation/main.py) → [comparison.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/user-memory-evaluation/comparison.py) → [evaluator.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/user-memory-evaluation/evaluator.py) → [metrics.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/user-memory-evaluation/metrics.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

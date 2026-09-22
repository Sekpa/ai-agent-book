# 计算一次完整任务的成本

[本章实验目录](../README.md) · [相关正文](../../book/chapter7.md) · [技术参考](REFERENCE.md)

模型单价较低，不一定意味着完成任务更便宜。多轮调用、重复读取历史和失败重试都可能增加总消耗。本实验把一条任务轨迹拆成逐次调用的成本。

## 理解实验

输入、缓存输入和输出通常需要分别计量，再按给定单价计算。轨迹中的用量是测量数据，价格是计算假设；更换价格只会重算同一轨迹，不代表另一模型会产生相同用量。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行已有轨迹的离线分析，找到成本最高的轮次。观察它是否重复输入了大量内容。随后使用技术参考中的自定义价格参数重算，理解价格与行为两个因素怎样分别影响总成本。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py --offline --scenario all
```

## 怎样解释结果

离线换单价不是跨模型性能实验。真实比较应让模型完成同一任务，再比较成功条件下的总支出、延迟和失败重试。

## 继续思考

如果减少一次调用却使任务失败率上升，平均每个成功任务的成本会怎样变化？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/agent-cost-analysis/demo.py) → [tracer.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/agent-cost-analysis/tracer.py) → [cost_efficiency_analyzer.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/agent-cost-analysis/cost_efficiency_analyzer.py) → [sample_trace.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/agent-cost-analysis/sample_trace.json)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

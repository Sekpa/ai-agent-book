# 压缩上下文时应该保留什么

[本章实验目录](../README.md) · [相关正文](../../book/chapter2.md) · [技术参考](REFERENCE.md)

随着搜索和工具调用增加，对话历史可能比当前任务需要的信息多得多。本实验比较几种压缩方法，学习怎样减少输入长度，同时保留继续完成任务所需的证据。

## 理解实验

压缩可以针对单条工具结果，也可以面向整段历史；有的方法还会根据当前目标决定保留什么。摘要更短并不自动更好：若丢掉来源、约束或尚未解决的问题，后续推理可能失去依据。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行策略列表命令，阅读每种方法的输入和输出，再配置模型运行单个策略。选择同一个研究问题做对照，保存压缩前后的消息，检查每次压缩发生的时机。最后才扩展到多策略批量比较。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python experiment.py --list-strategies
```

## 怎样解释结果

同时观察上下文长度、压缩本身的开销和最终答案的证据完整性。如果答案漏掉用户约束，沿轨迹找到约束最后一次出现的位置。一次低成本运行也可能只是提前结束任务，应结合完成质量解释结果。

## 继续思考

哪些信息适合被概括，哪些信息应该原样保留，例如精确数值、文件路径或工具调用标识？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[experiment.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/context-compression/experiment.py) → [compression_strategies.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/context-compression/compression_strategies.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/context-compression/agent.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

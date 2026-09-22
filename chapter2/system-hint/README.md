# 用状态提示帮助 Agent 记住当前进度

[本章实验目录](../README.md) · [相关正文](../../book/chapter2.md) · [技术参考](REFERENCE.md)

长任务中，Agent 可能忘记还剩多少预算、已经处理了哪些文件，或正在等待什么结果。本实验把这些运行状态整理成短提示，观察它们怎样帮助模型选择下一步。

## 理解实验

状态提示由程序根据真实运行状态生成，和模型自己写的计划不同。它适合提醒时间、进度与约束，但不能代替工具结果。提示内容放在哪里、多久更新，也会影响上下文长度与缓存复用。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行预览模式，看一条状态提示包含哪些字段。随后阅读它们从哪里取得数值，再配置模型运行一个示例任务。对照每轮提示与工具记录，确认提示中的进度确实来自已经发生的动作。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py --mode preview
```

## 怎样解释结果

观察模型是否减少重复操作、是否在预算耗尽前调整计划，而不是只看提示文字是否完整。过长或过于频繁的状态提示也可能分散注意力。比较时应保持任务不变，并记录额外输入成本。

## 继续思考

哪些状态应由程序计算，哪些判断适合留给模型？“任务已完成”应该由谁来确认？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[main.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/system-hint/main.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/system-hint/agent.py) → [view_trajectory.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/system-hint/view_trajectory.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

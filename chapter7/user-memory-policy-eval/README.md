# 检查 Agent 是否正确使用已经看到的记忆

[本章实验目录](../README.md) · [相关正文](../../book/chapter7.md) · [技术参考](REFERENCE.md)

记忆找到了，仍可能被用错。例如用户过去喜欢自动处理，现在却明确要求先确认。本实验把记忆直接交给 Agent，专门观察它在边界条件下会采取什么动作。

## 理解实验

轨迹前缀把任务停在关键决策之前，使不同表示方式可以在同一状态下比较。JSON、Markdown 和类似代码的记忆表示保留相同语义，区别主要在模型如何理解和使用这些条件。

## 动手之前

运行模型部分需要按技术参考配置对应的服务凭据；调用会使用该服务的额度。先准备一个小任务，再扩展比较范围。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先读一个用例中的记忆、当前要求与环境状态，写出应采取的下一步动作。配置模型后运行比较，逐项检查它是遵循当前要求、合理使用偏好，还是把旧记忆无限推广。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python runner.py --output results/tutorial-policy-prefix.json
```

## 怎样解释结果

这里不测检索召回率，也不是有无记忆的对照。评分应落在可观察动作上，而不是模型是否复述了记忆内容。

## 继续思考

一条偏好与当前明确指令冲突时，应保留记忆、更新记忆，还是只在本次任务中暂时不用？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[runner.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/user-memory-policy-eval/runner.py) → [cases.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/user-memory-policy-eval/cases.json)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

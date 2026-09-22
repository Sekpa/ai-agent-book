# 上下文怎样影响 Agent 的执行过程

[本章实验目录](../README.md) · [相关正文](../../book/chapter1.md) · [技术参考](REFERENCE.md)

假设模型刚用计算器得到一个结果，下一轮却看不到这条工具消息。它还能可靠地继续计算吗？本实验用同一任务的不同上下文版本，帮助你理解模型的行为为什么取决于它实际收到的信息。

## 理解实验

把一类信息从完整输入中移除，再比较行为，称为消融实验。这里分别考察历史消息、推理内容、工具定义和工具结果。它们承担不同职责：工具定义说明能做什么，工具结果说明刚才发生了什么；两者不能相互替代。

## 动手之前

运行模型部分需要按技术参考配置对应的服务凭据；调用会使用该服务的额度。先准备一个小任务，再扩展比较范围。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先为所选提供商配置 API Key。下面以百炼为例，只运行一道计算题。读完终端中的工具调用，再把命令里的 `full` 改成 `no_tool_results` 重跑。保持任务和模型相同，才能把差异与上下文变化联系起来。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py --mode single --provider dashscope --context-mode full --task "请调用计算器计算 (125 + 375) * 8，并给出结果。" --output full.json
```

## 怎样解释结果

算式的结果是 4000。先看模型有没有调用计算器，再看结果是否进入下一轮消息。即使两个答案都正确，也不能推断工具结果没有价值：简单算术可能被模型直接算对。如果没有发生工具调用，应换一个确实需要外部结果的任务。

## 继续思考

如果答案正确，但模型引用的是自己猜出的数据，你会把这次运行判为成功吗？还需要检查哪些证据？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[main.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/context/main.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/context/agent.py) → [grounding.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/context/grounding.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

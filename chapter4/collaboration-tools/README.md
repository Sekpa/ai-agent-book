# 让 Agent 把任务交给合适的协作者

[本章实验目录](../README.md) · [相关正文](../../book/chapter4.md) · [技术参考](REFERENCE.md)

有些任务需要另一个 Agent，有些需要用户作出决定，还有些只是等待外部事件。本实验把这些协作方式作为工具，学习主 Agent 怎样交出任务并接收结果。

## 理解实验

协作调用不仅传递一个问题，还需要明确上下文、预期结果和完成条件。过少的上下文使协作者无法判断，过多的上下文又增加成本和干扰。等待用户回复与等待子任务完成也应有不同的状态。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先列出工具目录，按用途区分子任务、人机协作和通知。再阅读技术参考中的本地演示，跟踪主任务何时等待、拿到什么结果、怎样恢复执行。通知类集成只在配置了明确接收对象后使用。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py list
```

## 怎样解释结果

检查结果是否足以让主任务继续，而不只看协作者是否返回了一段文字。对于需要用户决定的事项，应能辨认决定是否真正收到，不能把等待时间当作同意。

## 继续思考

把任务交给子 Agent 时，哪些背景必须提供，哪些信息可以让它自行查询？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[main.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/collaboration-tools/main.py) → [subagent_comparison.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/collaboration-tools/subagent_comparison.py) → [result_parsing.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/collaboration-tools/result_parsing.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

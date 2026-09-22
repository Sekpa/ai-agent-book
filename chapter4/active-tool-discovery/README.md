# 工具很多时，先寻找再调用

[本章实验目录](../README.md) · [相关正文](../../book/chapter4.md) · [技术参考](REFERENCE.md)

把全部工具说明一次塞进上下文，既占空间，也增加选择难度。本实验比较全量提供、检索预筛选和主动发现，学习如何让 Agent 在需要时找到合适的能力。

## 理解实验

主动发现把工具目录视为可查询资源：先获取候选说明，再决定调用哪个工具。这样减少一次暴露的信息，但增加了查找步骤，也可能漏掉真正需要的工具。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行离线演示，观察查询如何映射到候选工具。选一个需要多个能力的任务，记录每次发现了哪些说明。之后按技术参考配置模型与真实工具，比较三条路径。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py --offline
```

## 怎样解释结果

离线演示展示选择流程，不代表真实模型一定能选对。比较时同时检查工具覆盖、选择正确性、额外查找轮次和上下文消耗。

## 继续思考

如果所需工具从未进入候选列表，应该改目录说明、检索方法还是模型提示词？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[discovery.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/active-tool-discovery/discovery.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/active-tool-discovery/agent.py) → [tools_library.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/active-tool-discovery/tools_library.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 从缺少能力到接纳新的工具

[本章实验目录](../README.md) · [相关正文](../../book/chapter9.md) · [技术参考](REFERENCE.md)

面对一个现有工具无法完成的任务，Agent 可以寻找可用库并构造适配。本项目学习这条扩展路径中能力描述、接口适配与验证分别承担什么职责。

## 理解实验

新工具应明确输入、输出和依赖，经过验证后才进入能力目录。发现一个库与确认它适合当前环境是不同步骤；包装接口还可能改变错误处理与状态行为。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读工具管理器中候选工具的保存与加载方式，选择一个本地、无外部副作用的小能力作为练习。按技术参考检查适配与测试过程，观察失败时是否保留原有工具集合。

## 怎样解释结果

一次调用成功不足以说明工具可复用。应检查异常输入、依赖缺失和重复调用，并记录适用范围。来自网络的代码不能因为由 Agent 找到就自动获得信任。

## 继续思考

工具升级后返回结构发生变化，能力目录应怎样让使用方知道需要重新验证？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[tool_manager.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/self-evolving-tools/tool_manager.py) → [base_tools.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/self-evolving-tools/base_tools.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/self-evolving-tools/agent.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

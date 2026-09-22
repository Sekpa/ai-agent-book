# 在等待工具时继续处理其他工作

[本章实验目录](../README.md) · [相关正文](../../book/chapter6.md) · [技术参考](REFERENCE.md)

一个工具调用需要很久时，Agent 是否必须完全停住？异步执行让系统同时管理多个未完成动作，还需要应对中途取消和恢复。本实验把这三件事分开演示。

## 理解实验

并行可以缩短独立任务的总等待时间，但依赖关系仍必须保持。取消需要让尚未完成的工作停止或不再影响状态；检查点则保存可恢复的信息，使新会话知道哪些动作已经发生。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行并行演示，与串行用时比较。随后按技术参考依次运行中断和状态恢复示例，观察任务标识、取消事件与检查点内容。最后再接入模型，检查它怎样利用返回结果。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py parallel
```

## 怎样解释结果

演示中的加速取决于任务是否独立。恢复时还应检查重复动作和过期结果；一个已经取消的任务迟到返回，不应覆盖当前状态。

## 继续思考

两项并行任务都修改同一份文件时，还能直接并行吗？需要增加什么协调规则？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[runtime.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/async-agent/runtime.py) → [events.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/async-agent/events.py) → [tasks.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/async-agent/tasks.py) → [demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/async-agent/demo.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

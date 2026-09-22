# 让未完成的轨迹能够恢复执行

[本章实验目录](../README.md) · [相关正文](../../book/chapter5.md) · [技术参考](REFERENCE.md)

模型服务中断时，任务可能已经执行了一部分工具。直接重跑可能重复动作，切换模型又可能遇到消息格式差异。本实验讨论如何保留执行语义并恢复任务。

## 理解实验

轨迹中的工具调用与结果必须保持对应。不同提供商对推理内容和消息结构的要求可能不同，因此需要先明确哪些信息是任务状态，哪些是特定接口的表示。流式文本接续与工具轨迹接管也不是同一问题。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读中立轨迹表示，找到已经完成与尚未完成的动作。再按技术参考选择接管或文本接续路径，在可重复的样例任务中观察转换后的请求。接口约定具有版本条件，应与当前配置一起核对。

## 怎样解释结果

检查是否重复执行已有动作、丢失工具结果或把未完成文本当成完整答案。成功恢复一条轨迹只说明该路径兼容，不代表任意两家模型可以无条件互换。

## 继续思考

对于不能重复执行的动作，恢复逻辑应怎样知道它是否已经发生？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[neutral_trace.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/provider-failover/neutral_trace.py) → [renderers.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/provider-failover/renderers.py) → [run_handoff.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/provider-failover/run_handoff.py) → [run_continuation.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/provider-failover/run_continuation.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

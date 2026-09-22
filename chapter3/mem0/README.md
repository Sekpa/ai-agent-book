# 用 Mem0 管理跨会话记忆

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

引入记忆框架后，应用可以把信息提取与检索交给专门组件，但仍需理解框架实际保存了什么。本实验用 Mem0 连接对话与长期存储，观察一条信息怎样进入后续回答。

## 理解实验

记忆操作包含提取、写入、搜索和使用。应用还需要提供用户标识，把不同用户的数据隔离开来。框架返回的片段应经过语境核对，不能因为它被称为“记忆”就默认始终正确。

## 动手之前

运行模型部分需要按技术参考配置对应的服务凭据；调用会使用该服务的额度。先准备一个小任务，再扩展比较范围。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

按技术参考准备依赖、存储和模型凭据后，运行单用户演示。先输入一条清晰事实，再换一种问法查询；随后加入修正信息，观察存储与检索结果怎样变化。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py --mode demo --user-id demo_user
```

## 怎样解释结果

检查新增内容是否来自对话，检索是否命中了正确用户，以及旧事实是否仍影响回答。运行标准数据集时，还要区分记忆机制的效果和回答模型本身的能力。

## 继续思考

如果事实已经成功写入，但问答仍然失败，你会先检查检索条件还是模型上下文？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[main.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/mem0/main.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/mem0/agent.py) → [experiment.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/mem0/experiment.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 让 Agent 根据已有证据继续检索

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

一次检索往往只能回答问题的一部分。Agentic RAG 让模型根据当前证据决定是否追加检索、改写问题或查看相关条目。本实验关注多步取证与一次性检索的区别。

## 理解实验

每次检索都会改变模型下一轮能看到的信息。关键不是“检索次数多”，而是新检索是否填补了明确的证据缺口。若没有停止条件，Agent 也可能反复查找同一内容。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读离线比较程序中的问题和目标证据，再运行技术参考中的离线路径。选一道需要多个片段的问题，按轮次记录找到什么、还缺什么。之后配置模型和知识库，比较真实生成过程。

## 怎样解释结果

离线证据召回反映是否找到了指定材料，不能替代回答正确性。对于示例法律文本，还应核对来源与适用条件；这里练习的是检索方法，不应把模型输出直接作为现实事务的处理依据。

## 继续思考

模型应凭什么判断已经找齐证据，而不是因为输出长度或调用次数到了上限就结束？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[compare_offline.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/agentic-rag/compare_offline.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/agentic-rag/agent.py) → [tools.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/agentic-rag/tools.py) → [offline_retriever.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/agentic-rag/offline_retriever.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

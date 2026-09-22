# 跨多次对话寻找回答所需的记忆

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

用户问“按我上次的偏好安排吧”，相关偏好可能散落在多次对话中。本实验把 Agentic RAG 用在用户记忆上，学习怎样通过多步检索补齐背景。

## 理解实验

检索一次得到的信息可能只是线索，例如某次旅行的时间。Agent 需要利用线索继续寻找预算、同行者或后续修改。原始对话提供出处，不能把一次检索到的旧偏好直接当成当前事实。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行离线示例，比较多步路径与简单召回。对每个返回片段标记它回答了问题的哪一部分。再按技术参考接入模型和检索后端，用同一用户的多轮记录观察查询怎样变化。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py --mode offline-demo
```

## 怎样解释结果

检查是否找齐了必要片段、是否混入其他用户的内容，以及后来的修改有没有覆盖旧信息。离线示例展示检索结构，真实模型是否会提出同样的查询，需要另行观察。

## 继续思考

用户先说喜欢海边，后来取消旅行计划，系统应保留哪些记忆，又应怎样避免过时建议？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[offline_demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/agentic-rag-for-user-memory/offline_demo.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/agentic-rag-for-user-memory/agent.py) → [chunker.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/agentic-rag-for-user-memory/chunker.py) → [indexer.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/agentic-rag-for-user-memory/indexer.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

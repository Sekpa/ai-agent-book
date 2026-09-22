# 同时保存对话证据与结构化用户记忆

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

“他已经改了时间”这样的句子离开对话很难理解，而单独保存“周三开会”又可能丢掉来源。本实验结合带背景的对话检索和结构化记忆卡片，学习两种表示如何互补。

## 理解实验

对话片段保留具体语境，记忆卡片便于查询相对稳定的事实。背景前缀帮助检索定位人物与事件；卡片则需要记录更新和冲突。两层信息应能相互核对，而不是各自形成一套无法追溯的结论。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读 `contextual_compare.py` 中的对照方式，再选一组存在后续修正的对话。观察原始片段、补充背景和记忆卡片分别保存了什么。按技术参考准备后端后，再运行模型驱动的问答比较。

## 怎样解释结果

除了答案是否正确，还要检查引用的是哪次对话、记忆有没有时间条件，以及一条错误摘要是否被多层重复放大。更多记忆不一定更好，关键是能否取到当前问题需要的证据。

## 继续思考

如果卡片与原始对话冲突，应优先采用哪一个？系统应怎样向读者解释不确定性？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[contextual_compare.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/contextual-retrieval-for-user-memory/contextual_compare.py) → [contextual_indexer.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/contextual-retrieval-for-user-memory/contextual_indexer.py) → [advanced_memory_manager.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/contextual-retrieval-for-user-memory/advanced_memory_manager.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

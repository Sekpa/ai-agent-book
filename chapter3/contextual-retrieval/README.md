# 给孤立片段补上检索所需的背景

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

文档中的“该规定”或“上述方法”离开上下文后常常难以理解。本实验在建立索引前给片段补充简短背景，观察检索能否更准确地找到它。

## 理解实验

背景前缀说明片段属于哪份文档、讨论什么主题。它可以让原本缺少关键词的片段更容易被检索，但生成的背景也可能错误，或让多个片段变得过于相似。因此需要同时检查召回变化与前缀内容。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行逐查询比较，选择一条普通分块漏检、补充背景后命中的案例。阅读原文、分块和前缀，解释多出的文字为什么有帮助。再选择一条没有改善的案例，寻找这种方法的边界。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python compare_retrieval.py --per-query
```

## 怎样解释结果

下方比较使用已有数据；它不能代表重新生成前缀的成本。需要评估完整流程时，还要计入前缀生成、重新索引和存储开销，并防止前缀包含测试问题的答案。

## 继续思考

一个背景前缀加入了原文没有的信息，即使提高召回率，是否仍应保留？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[compare_retrieval.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/contextual-retrieval/compare_retrieval.py) → [contextual_tools.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/contextual-retrieval/contextual_tools.py) → [chunking.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/contextual-retrieval/chunking.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 用层次结构和关系图组织知识

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

有些问题只需一个段落，有些问题却要跨越多个章节。把文档切成平坦片段未必足够。本实验比较层次摘要与知识关系图，学习怎样为不同问题组织检索路径。

## 理解实验

RAPTOR 将片段逐层聚合成摘要，便于从全局主题走向细节；GraphRAG 将实体与关系连接起来，便于沿关联追踪证据。两者都依赖构建阶段的质量，结构本身不能保证摘要或关系正确。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行不需要模型凭据的 `demo`，比较示意索引怎样组织材料；它不构建真实 RAPTOR 或 GraphRAG 索引。再阅读两种索引器的构建流程。准备自己的文档后，先检查少量节点和对应原文，确认结构没有失真，再扩展到完整索引。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py demo
```

## 怎样解释结果

回答涉及多个概念时，追踪证据经过哪些节点。层次摘要可能压掉细节，关系抽取也可能引入不存在的联系。应能从最终答案回到原始片段，而不只停留在生成的摘要上。

## 继续思考

“某功能在哪里定义”和“几种功能有什么共同设计”分别更适合怎样的检索入口？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[main.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/structured-index/main.py) → [raptor_indexer.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/structured-index/raptor_indexer.py) → [graphrag_indexer.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/structured-index/graphrag_indexer.py) → [hybrid_retriever.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/structured-index/hybrid_retriever.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

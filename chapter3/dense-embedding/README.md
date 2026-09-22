# 把文本变成向量后怎样检索

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

用户的问题与文档用词不同，仍可能表达相同含义。稠密检索把文本编码成向量，再根据向量之间的距离寻找候选内容。本实验让你分别观察语义表示和近似搜索的作用。

## 理解实验

嵌入模型决定文本怎样映射到空间；索引决定怎样高效寻找邻近向量。ANNOY 和 HNSW 等近似索引通过减少搜索工作提高速度，但可能漏掉精确搜索会返回的邻居。索引召回与问答质量不是同一个指标。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行合成向量上的索引比较，不需要下载嵌入模型。理解速度与召回的关系后，再按技术参考准备本地嵌入模型，使用自然语言查询示例语料。保持模型相同，比较不同索引的返回结果。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python cli.py --compare-ann -k 10
```

## 怎样解释结果

合成向量实验只能解释索引行为，不能证明文本语义效果。文本查询还应检查相关片段是否被编码得足够接近，以及相似但事实不同的片段是否被误排在前面。

## 继续思考

若索引几乎找回了全部近邻，最终检索结果仍不相关，问题可能出在哪一层？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[cli.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/dense-embedding/cli.py) → [embedding_service.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/dense-embedding/embedding_service.py) → [indexing.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/dense-embedding/indexing.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 组合关键词检索、向量检索与重排序

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

关键词检索擅长精确词项，向量检索擅长语义相近表达。混合检索尝试结合两者，再用重排序模型细看候选。本实验按阶段观察文档如何进入、离开最终结果列表。

## 理解实验

流水线先召回候选，再融合不同来源的排名，最后重排。后续阶段通常只能处理已有候选，因此前面漏掉的文档难以靠重排补回。把最终指标拆到各阶段，才能知道应该改召回还是排序。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行仅含 BM25 的离线路径，建立可理解的基线。然后按技术参考启动稠密检索服务和重排模型，逐个加入阶段。每次只改一项，并保留同一查询的候选列表。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python evaluate.py --no-dense --no-rerank
```

## 怎样解释结果

比较候选覆盖、正确文档排名和耗时。若召回提高但首位结果变差，要检查融合权重与去重；若重排没有改善，先确认正确文档已经进入候选集。

## 继续思考

应该优先增加候选数量，还是换更强的重排模型？你需要哪些阶段数据才能决定？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[evaluate.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/retrieval-pipeline/evaluate.py) → [retrieval_pipeline.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/retrieval-pipeline/retrieval_pipeline.py) → [fusion.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/retrieval-pipeline/fusion.py) → [reranker.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/retrieval-pipeline/reranker.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 从案例中抽取因素并形成可检索知识

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

一批案例可能反复出现相同的影响因素，但这些因素未必已经被整理成表格。本实验以案例文本为材料，学习从发现字段到结构化抽取，再到归纳典型模式的过程。

## 理解实验

流程先提出候选因素，再把每份材料转成结构化记录，最后聚类并总结原型。每一步都可能引入误差：遗漏因素、抽取错误或不合适的聚类，都可能被后续摘要掩盖。

## 动手之前

运行模型部分需要按技术参考配置对应的服务凭据；调用会使用该服务的额度。先准备一个小任务，再扩展比较范围。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读仓库自带的教学样例，人工标注几条你认为重要的因素，再配置模型运行 `demo.py`。比较模型发现的字段与人工标注，并检查几条记录如何归入同一原型。真实数据路径与教学数据路径的准备方式见技术参考。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py
```

## 怎样解释结果

相似案例的归类不能直接推出因果规律。应使用未参与归纳的材料检查原型是否仍有解释力，并保留回到原文的路径。法律场景中的输出在这里仅用于研究知识组织方法。

## 继续思考

一个因素在训练样例里经常出现，却在新样例中无帮助，怎样判断它是规律还是数据偏差？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[discovery.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/structured-knowledge-extraction/discovery.py) → [extractor.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/structured-knowledge-extraction/extractor.py) → [archetypes.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/structured-knowledge-extraction/archetypes.py) → [demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/structured-knowledge-extraction/demo.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

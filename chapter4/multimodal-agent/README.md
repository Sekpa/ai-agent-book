# 比较直接看图与先提取文本

[本章实验目录](../README.md) · [相关正文](../../book/chapter4.md) · [技术参考](REFERENCE.md)

回答图表问题时，模型可以直接读取图像，也可以先通过工具提取文字和数据。本实验比较几种输入路径，学习选择方式时需要考虑哪些信息可能丢失。

## 理解实验

直接多模态输入保留视觉布局，文本抽取便于后续检索与计算，工具化分析还可以针对局部内容处理。每条路径都会改变模型看到的材料，因而不能只比较最终回答长度。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行样例生成器，打开生成的图表与报告，人工确认正确答案。随后按技术参考配置模型，对同一文件提出同一问题，分别观察直接读取、提取文本和工具分析的过程。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python create_sample.py
```

## 怎样解释结果

如果读错数值，检查坐标轴、单位和图例有没有保留；如果漏掉关系，检查文本抽取是否丢失布局。示例正确不代表任意扫描件或复杂表格都适用。

## 继续思考

哪些问题只需要文字，哪些问题必须保留版面或空间关系？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[create_sample.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/multimodal-agent/create_sample.py) → [demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/multimodal-agent/demo.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/multimodal-agent/agent.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

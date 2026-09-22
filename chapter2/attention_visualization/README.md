# 读懂注意力热力图

[本章实验目录](../README.md) · [相关正文](../../book/chapter2.md) · [技术参考](REFERENCE.md)

当模型处理一句话时，不同位置会以不同权重读取已有位置的信息。注意力热力图把这些权重画出来，帮助你把抽象的矩阵计算与具体词元联系起来。

## 理解实验

图中的行通常对应正在计算的位置，列对应被读取的位置。层和注意力头不同，图案也会不同。因果模型不能读取未来位置，因此图中的遮挡区域首先反映模型结构，而不是某个词“没有意义”。

## 动手之前

本节需要本地模型或服务。先按技术参考确认模型文件、运行后端与内存或显存要求，再进行下面的练习。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先准备参考文档中的本地模型依赖，运行默认命令得到一张热力图。确认横纵轴与词元的对应关系，再只改变一个变量：提示词、层或注意力头。先比较一对图，最后再查看跨层视图。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python attention_cli.py
```

## 怎样解释结果

某个位置颜色深，表示它在所选层和头中获得较大注意力权重，不能直接解释为它对最终答案最重要。还要区分提示词内部的注意力和生成阶段的注意力；把多个头平均后，一些局部结构也会被隐藏。

## 继续思考

若同一个词在不同层获得不同权重，能否用一张热力图概括模型对它的全部处理？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[attention_cli.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/attention_visualization/attention_cli.py) → [visualization.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/attention_visualization/visualization.py) → [run_attention_experiment.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/attention_visualization/run_attention_experiment.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

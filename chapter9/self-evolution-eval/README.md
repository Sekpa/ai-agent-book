# 评价学习、迁移、修订与保持

[本章实验目录](../README.md) · [相关正文](../../book/chapter9.md) · [技术参考](REFERENCE.md)

真正的持续进化不只是同一道题第二次做对。系统还应把规律用于新任务，适应规则变化，并保留没有过时的能力。本实验通过顺序任务流分别观察这些阶段。

## 理解实验

学习阶段提供经验，迁移阶段改变表述或环境，规则变化阶段要求更新，保持阶段检查旧能力。按顺序运行才能看到状态积累的影响；把每题独立重置会改变研究对象。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行参考策略演示，阅读任务流中的阶段划分。找出某条规则何时出现、何时失效。理解评价逻辑后，再按技术参考运行真实模型比较。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py --profile all --output output/reference-report.json
```

## 怎样解释结果

参考策略分数用于检查评估框架，不代表真实模型能力。汇总时应分别报告学会、迁移、忘记旧规则与保留有效规则的表现。

## 继续思考

一个系统在新规则上进步，却忘掉仍有效的旧规则，应该怎样描述它的变化？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[dataset.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/self-evolution-eval/dataset.json) → [harness.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/self-evolution-eval/harness.py) → [demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/self-evolution-eval/demo.py) → [run_experiment_9_9.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/self-evolution-eval/run_experiment_9_9.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

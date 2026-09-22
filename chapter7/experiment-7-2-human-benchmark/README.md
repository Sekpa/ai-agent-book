# 通过亲自走任务理解基准难度

[本章实验目录](../README.md) · [相关正文](../../book/chapter7.md) · [技术参考](REFERENCE.md)

只看基准总分，很难知道一道任务需要哪些操作。本项目选取不同难度的任务，保留逐步操作轨迹，让你从案例理解环境、成功条件与失败原因。

## 理解实验

任务体验可以揭示评分规则没有直接表达的困难，例如信息入口不明显或操作步骤很长。但个别操作者的路径只是一个样本，不能直接等同于人类平均水平。本目录既有记录由模型操作，应按模型轨迹理解。

## 动手之前

本节先通过代码和已有记录理解机制；不需要连接外部目标或执行真实业务操作。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先从选择清单中挑一道简单任务，阅读目标后独立想出操作路线，再与已有轨迹比较。随后看一道失败任务，判断失败来自理解、工具操作还是环境。重跑外部任务的环境要求见技术参考。

## 怎样解释结果

保留第一次失败有助于理解真实难点。不要把修复后的结果替换原始记录，也不要将模型执行记录表述成人类被试实验。

## 继续思考

如果要正式建立人类基线，除了任务选择，还需要怎样记录参与者背景、时间限制和尝试次数？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[selection_manifest.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/experiment-7-2-human-benchmark/selection_manifest.json) → [results.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/experiment-7-2-human-benchmark/results.json) → [run_android_human.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/experiment-7-2-human-benchmark/run_android_human.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

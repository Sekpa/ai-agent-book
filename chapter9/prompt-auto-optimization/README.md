# 用最小提示词改动修正已定位的失败

[本章实验目录](../README.md) · [相关正文](../../book/chapter9.md) · [技术参考](REFERENCE.md)

让模型把提示词“润色一下”，很难知道变化是否有效。本实验从客服失败中提取诊断，再生成具体规则的最小修改，学习怎样评价提示词更新。

## 理解实验

补丁应说明由哪些案例触发、修改哪条规则以及预期改变什么行为。边界集检查问题是否改善，保留集检查旧任务是否退化。两类结果共同决定候选是否值得采用。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读一条过度转接案例与对应诊断，定位原提示中含糊的规则。按技术参考配置模型后生成候选补丁，比较修改前后文本，再查看两组评估的逐题变化。

## 怎样解释结果

文字更顺不代表行为更好。空补丁、无法追溯来源的修改和只在旧失败样本上有效的修改都需要另行判断。工作副本与原始提示应分开保存。

## 继续思考

一个补丁解决了边界案例，却让普通任务更容易拒绝，应该继续扩大补丁还是回退重找原因？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[learning_signal.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/prompt-auto-optimization/learning_signal.py) → [coding_agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/prompt-auto-optimization/coding_agent.py) → [release_gate.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/prompt-auto-optimization/release_gate.py) → [evaluate.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/prompt-auto-optimization/evaluate.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

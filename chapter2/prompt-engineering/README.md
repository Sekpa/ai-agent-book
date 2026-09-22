# 用对照实验理解提示词设计

[本章实验目录](../README.md) · [相关正文](../../book/chapter2.md) · [技术参考](REFERENCE.md)

提示词不仅告诉模型任务是什么，还说明业务规则、工具用途和遇到困难时的处理方式。本实验通过改变提示词的部分内容，观察这些信息怎样影响一个客服 Agent 的决策。

## 理解实验

消融的关键是控制变量。语气、规则组织和工具描述属于不同维度；若同时换模型、改任务和改提示词，即使成功率变化，也难以判断原因。τ-bench 环境提供任务与结果检查，使比较不只依赖人工阅读回答。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先在技术参考中了解任务环境和各组提示词差异，再阅读一次任务的规则与目标。配置模型后，从少量任务开始运行 `run_ablation.py`。对照完整轨迹，找出某条规则影响工具选择或业务操作的具体位置，再扩大样本。

## 怎样解释结果

回答礼貌不等于业务操作正确。检查任务最终状态、规则遵循和工具参数，再看总体成功率。少量任务中的领先可能来自随机性；复测应保持任务集一致，并报告多次运行的差异。

## 继续思考

若删除一段规则后成绩反而提高，可能是规则冗余、表达冲突，还是任务集没有覆盖它的作用？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[run_ablation.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/prompt-engineering/run_ablation.py) → [ablation_agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/prompt-engineering/ablation_agent.py) → [ablation_utils.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/prompt-engineering/ablation_utils.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

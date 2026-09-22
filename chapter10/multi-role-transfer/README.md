# 比较角色切换与按需加载技能

[本章实验目录](../README.md) · [相关正文](../../book/chapter10.md) · [技术参考](REFERENCE.md)

一个任务可能先需要分析，再需要编码或审核。实现多角色行为时，可以切换系统提示与工具，也可以保持统一角色并加载技能。本实验比较这两种组织方式。

## 理解实验

角色切换改变当前行为约束，技能加载则向共享轨迹追加任务说明。两者保留与暴露的信息不同，因而会影响上下文成本、职责边界和后续决策。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读一条任务，标出它需要哪些职责，再查看角色定义与技能说明。配置模型后按技术参考运行同一任务的两种路径，对照角色变化时消息和工具目录怎样改变。

## 怎样解释结果

最终成功率、职责遵循和上下文开销应分别比较。角色名称更多不等于分工更清楚，反复切换也可能增加干扰。

## 继续思考

如果审核角色仍能直接修改它正在审核的结果，角色切换是否真正建立了独立检查？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[roles.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/multi-role-transfer/roles.py) → [orchestrator.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/multi-role-transfer/orchestrator.py) → [tools.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/multi-role-transfer/tools.py) → [evaluation.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/multi-role-transfer/evaluation.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

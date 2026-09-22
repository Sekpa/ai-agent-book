# 从失败案例提炼可以迁移的规则

[本章实验目录](../README.md) · [相关正文](../../book/chapter9.md) · [技术参考](REFERENCE.md)

客服 Agent 可能太早转人工，也可能在需要帮助时反复尝试。本实验从失败轨迹提炼转接和工具使用规则，学习怎样把经验变成可复用指令。

## 理解实验

提炼集负责发现规律，迁移集负责检查新任务是否受益。两者分开，才能减少对已有错误的记忆。规则还应描述适用条件，而不是把一个案例的具体步骤写成所有任务都要执行的命令。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读一条转接失败轨迹，写出触发条件、错误动作和更合适的处理方式。按技术参考准备 τ²-bench 后，在提炼集生成规则，再在未见任务上比较原策略与修改策略。

## 怎样解释结果

转人工更少不一定更好，有些任务本来就需要转接。应同时检查任务解决、规则遵循和不必要转接，保留规则不适用的案例。

## 继续思考

一条经验在旧环境中成立，但工具能力后来增强了，怎样决定它是否还应继续使用？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[derive_rules.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/tau2-escalation-experience/derive_rules.py) → [analyze.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/tau2-escalation-experience/analyze.py) → [run_arms.sh](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/tau2-escalation-experience/run_arms.sh)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

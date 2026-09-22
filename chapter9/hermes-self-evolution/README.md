# 让 Agent 阅读设计知识后提出自身改进

[本章实验目录](../README.md) · [相关正文](../../book/chapter9.md) · [技术参考](REFERENCE.md)

Agent 读完工程知识，能否发现自身实现中的不足，并把建议变成可验证变化？本实验将阅读、源码分析、修改与后续评估连接起来。

## 理解实验

开放式选题允许 Agent 自己提出改进方向，但判断价值仍需要外部依据。补丁可运行只是第一步，还要用下游任务比较修改前后的行为，区分增加功能与改善能力。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读给 Agent 的任务和一次候选改进说明，检查它引用了哪些书中概念与代码事实。按技术参考准备独立源码副本后运行，再跟踪审查意见怎样进入下一轮修改。

## 怎样解释结果

不要把读后总结当作能力提升。应检查真实代码变化、测试与下游对照；删除候选功能的消融比较有助于判断收益是否来自该改动。

## 继续思考

Agent 自己提出的改进目标，应该由谁定义通过条件，才能避免它只挑容易证明成功的目标？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[run_experiment_9_8.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/hermes-self-evolution/run_experiment_9_8.py) → [run_review_pass.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/hermes-self-evolution/run_review_pass.py) → [run_downstream_ablation.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/hermes-self-evolution/run_downstream_ablation.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 从界面任务失败提出可检验的改进

[本章实验目录](../README.md) · [相关正文](../../book/chapter7.md) · [技术参考](REFERENCE.md)

Android 操作中，一次点击失败可能来自观察错误、等待不足或目标识别不准。本实验以固定任务作成对比较，学习如何让改进假设与具体失败对应。

## 理解实验

先提出明确假设，再在相同任务与种子下比较基线和候选。若同时改变多个策略，结果难以归因。环境准备也需要固定，否则模拟器差异可能被误认为 Agent 改善。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读一个任务的目标状态和失败轨迹，写出可被反驳的解释。按技术参考准备 AndroidWorld 与设备环境，从少量成对任务开始运行。对照截图、动作和状态检查，寻找候选具体改变了哪一步。

## 怎样解释结果

单个任务通过可能只是偶然。应检查改善是否重复出现、是否对其他任务造成退化，以及测试集合是否被反复用于挑选策略。

## 继续思考

如果增加等待时间提高了成功率，怎样判断是修正必要同步，还是只掩盖了识别错误？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[run_controlled_experiment.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/android-world/run_controlled_experiment.py) → [experiment_core.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/android-world/experiment_core.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

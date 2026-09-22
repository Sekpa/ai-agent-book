# 用可重放证据检验故障解释

[本章实验目录](../README.md) · [相关正文](../../book/chapter5.md) · [技术参考](REFERENCE.md)

日志里看到异常之后，很容易写出一个听起来合理的原因。本实验进一步要求诊断能够对应系统结构，并通过重放与回归检查得到支持。

## 理解实验

轨迹说明发生了什么，架构与需求说明本来应该发生什么。诊断把两者比较，提出可验证的假设，再生成检查用例。如果重放不能支持假设，应回到证据重新判断。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读样例轨迹和需求说明，自己提出一个可能原因，再按技术参考运行本地诊断。检查报告引用了哪些事件，以及测试是否真正覆盖这些事件。发布到 GitHub 是独立的可选步骤，学习本地诊断无需开启它。

## 怎样解释结果

重放失败可能来自环境差异，也可能说明诊断错误。报告应区分已观察事实与推测，并解释测试通过后究竟排除了哪些可能性。

## 继续思考

两个不同缺陷产生相似错误日志时，你会设计什么额外观察来区分它们？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[diagnoser.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/log-diagnosis/diagnoser.py) → [replay.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/log-diagnosis/replay.py) → [sut.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/log-diagnosis/sut.py) → [demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/log-diagnosis/demo.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

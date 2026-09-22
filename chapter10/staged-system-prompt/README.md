# 按任务阶段组织行为与工具

[本章实验目录](../README.md) · [相关正文](../../book/chapter10.md) · [技术参考](REFERENCE.md)

同一个编码任务在分析、实现和审核阶段需要不同注意力。本补充案例用阶段化提示与工具集合，帮助理解一种显式组织工作过程的方法；它已不属于当前正文的编号实验。

## 理解实验

阶段切换改变当前职责与可用动作，共享轨迹则保留前面取得的证据。划分阶段可以帮助聚焦，也可能在切换过早时打断必要探索，因此需要明确进入和退出条件。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读阶段定义，拿一个小任务标出分析何时足够、实现何时结束、审核检查什么。按技术参考运行演示，对照每次阶段切换前后的上下文和工具变化。

## 怎样解释结果

进入审核阶段不等于实现已经正确，阶段名称也不能替代完成检查。观察系统是否允许根据新证据返回前一阶段，以及返回后是否保留了已有工作。

## 继续思考

如果审核发现需求理解错误，应该只修改代码，还是回到分析阶段重新确认目标？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[config.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/staged-system-prompt/config.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/staged-system-prompt/agent.py) → [tools.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/staged-system-prompt/tools.py) → [demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/staged-system-prompt/demo.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 观察记忆、计划与互动如何形成群体行为

[本章实验目录](../README.md) · [相关正文](../../book/chapter10.md) · [技术参考](REFERENCE.md)

多个角色在同一个虚拟世界中生活，会产生怎样的交流与计划变化？本项目以 Generative Agents 环境为例，学习个体记忆机制与群体行为之间的联系。

## 理解实验

角色根据观察形成记忆，通过检索与反思生成计划，再与环境和其他角色互动。看起来连贯的故事可能由这些局部机制产生，但不能只凭叙事合理就证明每个机制都有效。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先选择一个角色，按时间阅读它的观察、记忆和计划，再查看一次交互怎样改变后续行动。按技术参考准备外部世界与模型接口后，比较保留或移除某个机制时的差异。

## 怎样解释结果

模拟世界的步长、初始人物设定和模型都会影响结果。需要区分计划被写出与行动实际发生，并保留不连贯或未完成的案例。

## 继续思考

如果角色的计划很合理，却频繁没有执行，应该检查记忆检索、计划更新还是环境动作？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[experiment_protocol.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/generative-agents/experiment_protocol.json) → [launch_campaigns.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/generative-agents/launch_campaigns.py) → [analyze_campaign.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/generative-agents/analyze_campaign.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

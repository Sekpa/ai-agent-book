# 把明确的业务规则放进代码

[本章实验目录](../README.md) · [相关正文](../../book/chapter5.md) · [技术参考](REFERENCE.md)

客服 Agent 需要同时理解用户意图和遵守退款条件。若所有规则都写在提示词里，模型可能在复杂对话中漏掉一项。本实验比较自然语言规则与代码检查的作用。

## 理解实验

适合代码化的是可明确判定的条件，例如状态、时间范围或资格。模型负责把用户需求映射到操作，代码负责检查操作是否满足规则。规则移入程序后，仍需要正确的数据和参数。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先读航空业务环境中的退款规则，人工判断一个可退款与一个不可退款案例。再按技术参考运行两种配置，对照模型提出的动作和执行层的判断。重点观察同一请求在两条路径中何时被接受或拒绝。

## 怎样解释结果

拒绝了违规操作，不等于已经帮助用户解决问题；应继续检查模型是否解释原因或提供可行选项。代码化规则也可能写错，因此需要独立于模型的规则用例。

## 继续思考

哪些政策适合确定性检查，哪些仍需要上下文判断或人工处理？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/small-model-codified-rules/demo.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/small-model-codified-rules/agent.py) → [airline_env.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/small-model-codified-rules/airline_env.py) → [tasks.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/small-model-codified-rules/tasks.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

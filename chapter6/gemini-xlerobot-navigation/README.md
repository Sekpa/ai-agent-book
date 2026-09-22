# 比较执行前观察与执行后验证

[本章实验目录](../README.md) · [相关正文](../../book/chapter6.md) · [技术参考](REFERENCE.md)

把杯子放进托盘，可能因为抓取失败而没有真正完成。本实验在桌面模拟任务中比较闭环策略，学习为什么计划之后还需要观察与验证。

## 理解实验

高层策略通过观察、抓取、放置、验证和停止等工具控制过程。环境可以按设定概率引入失败，使你比较不检查结果与根据结果调整的差别。工具契约保持固定，减少其他因素干扰。

## 动手之前

先在模拟或回放路径中理解流程。真实设备的连接、标定与运行条件见技术参考，模拟结果与真机结果应分别解释。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先读一条把杯子放进托盘、把纸放入垃圾盒的任务轨迹。再按技术参考运行模拟，逐步提高失败概率，观察不同策略何时发现失败、是否重试以及最终状态。

## 怎样解释结果

多调用几次工具只有在带来有效纠正时才有价值。成功率应与动作数和失败条件一起解释；模拟器中的改善还需要真机验证，才能说明现实控制效果。

## 继续思考

每一步都验证与只在最后验证，分别会增加什么成本，又可能漏掉什么信息？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[desktop_planner.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/gemini-xlerobot-navigation/desktop_planner.py) → [xlerobot_tool_contract.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/gemini-xlerobot-navigation/xlerobot_tool_contract.py) → [validate_evidence.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/gemini-xlerobot-navigation/validate_evidence.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 把反复出现的控制错误定位到代码

[本章实验目录](../README.md) · [相关正文](../../book/chapter9.md) · [技术参考](REFERENCE.md)

工具已经说明错误不可重试，Agent 却仍重复调用，这可能是控制逻辑的问题。本实验学习如何从这类轨迹提出代码修改，并验证候选没有破坏其他行为。

## 理解实验

重试、熔断和停止条件属于运行控制。候选代码应在独立环境中执行测试，改进证据来自失败用例与正常用例的共同结果。模型提出补丁与补丁被采用是两个阶段。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读失败轨迹，找到不可重试标记出现后仍继续调用的位置。再检查现有控制逻辑与测试。按技术参考准备隔离执行环境和模型后，生成候选并查看它如何改变重试分支。

## 怎样解释结果

少一次调用不一定正确：可重试错误仍可能需要恢复。测试应同时覆盖继续、停止和超时，并说明候选能修改的范围。

## 继续思考

若模型用“一律不重试”通过了失败用例，还需要什么保留用例才能发现这种退化？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[failure_trajectories.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/self-modifying-agent/failure_trajectories.json) → [evolution.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/self-modifying-agent/evolution.py) → [candidate_sandbox.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/self-modifying-agent/candidate_sandbox.py) → [run_experiment_9_6.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/self-modifying-agent/run_experiment_9_6.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

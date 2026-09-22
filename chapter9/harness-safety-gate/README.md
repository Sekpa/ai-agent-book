# 把用户纠正转成执行前的确认规则

[本章实验目录](../README.md) · [相关正文](../../book/chapter9.md) · [技术参考](REFERENCE.md)

用户指出“这类操作应该先问我”，说明系统可能缺少执行前的约束。本实验将反馈转成候选确认规则，学习怎样修正流程，而不只提醒模型更谨慎。

## 理解实验

确认门禁位于工具调度前，依据动作及其参数判断是否需要用户决定。生成规则后，需要同时检查应拦截的动作和应正常放行的任务，避免过度确认使系统无法使用。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读反馈样例，说明哪些操作需要确认以及原因。运行本地演示，跟踪动作请求、确认状态和执行决定。再查看边界用例与保留用例怎样评价候选规则。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py
```

## 怎样解释结果

模型说“已确认”不能代替实际收到用户决定。还要检查确认是否对应当前参数，参数变化后旧确认能否继续使用。

## 继续思考

用户同意一次操作后，系统应允许哪些重复动作，又应在什么变化下重新确认？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[safety_policy_gate.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/harness-safety-gate/safety_policy_gate.py) → [evolution.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/harness-safety-gate/evolution.py) → [boundary_cases.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/harness-safety-gate/boundary_cases.json) → [retention_cases.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/harness-safety-gate/retention_cases.json)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

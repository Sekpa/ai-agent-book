# 用游戏状态机协调多角色语音交互

[本章实验目录](../README.md) · [相关正文](../../book/chapter10.md) · [技术参考](REFERENCE.md)

狼人杀同时包含公开发言、私有信息、回合规则和多人决策，适合观察多 Agent 协调。本实验将确定的游戏规则交给代码，把角色表达与选择交给模型。

## 理解实验

裁判状态机负责阶段、技能、死亡与胜负，角色只接收各自允许看到的信息。语音是交互通道，不能改变信息边界。独立用户模拟器与真人参与也需要明确区分。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行离线演示，跟踪一轮夜晚、白天与投票，检查不同角色看到的信息。随后按技术参考接入真实模型与语音路径，再观察表达、选择和裁判状态是否一致。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py --offline
```

## 怎样解释结果

离线路径是确定性示例，不代表真实对话质量。多角色游戏还应检查私有信息泄漏、同时死亡与技能消耗等边界，而不只看最后是否分出胜负。

## 继续思考

一个角色在公开发言中声称知道私有信息，怎样判断这是游戏内推测还是系统真的泄露了上下文？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/voice-werewolf/demo.py) → [validate_simulator_run.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/voice-werewolf/validate_simulator_run.py) → [evaluate_audio_run.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/voice-werewolf/evaluate_audio_run.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

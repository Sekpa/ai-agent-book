# 在相同场景中比较动作分块策略

[本章实验目录](../README.md) · [相关正文](../../book/chapter7.md) · [技术参考](REFERENCE.md)

视觉动作模型可以一次预测一个动作，也可以预测一段动作。更长的动作块减少决策频率，却可能降低及时纠正的能力。本实验在同一仿真任务上比较两种设置。

## 理解实验

成对使用相同场景种子，可以减少初始状态差异带来的干扰。训练分布内与分布外场景分别评价，帮助判断结果能否迁移。超时与其他失败应明确区分。

## 动手之前

本节需要本地模型或服务。先按技术参考确认模型文件、运行后端与内存或显存要求，再进行下面的练习。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先按技术参考准备固定版本的仿真环境与模型检查点，运行环境预检查。再选择一个场景观察两种动作分块的轨迹，理解每次观察与动作之间的间隔，最后扩展到成组比较。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python experiment.py preflight
```

## 怎样解释结果

动作块较长后成功率提高，不等于所有任务都应使用长动作块。应结合任务速度、误差累积和视频中的纠正行为分析。一次完整运行也可能得到低成功率，这仍是有价值的结果。

## 继续思考

当物体突然移动时，长动作块与短动作块分别可能怎样响应？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[config.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/openvla-robotwin2-eval/config.json) → [experiment.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/openvla-robotwin2-eval/experiment.py) → [finalize_evidence.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/openvla-robotwin2-eval/finalize_evidence.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

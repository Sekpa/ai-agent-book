# 用偏好对训练更可靠的完成判断

[本章实验目录](../README.md) · [相关正文](../../book/chapter8.md) · [技术参考](REFERENCE.md)

编码 Agent 可能没有运行检查就宣布完成。这个问题适合放在“即将结束”的决策点上分析：它应该直接收尾，还是先核对尚未满足的条件？

## 理解实验

DPO 使用同一上下文下的偏好响应对。这里把未经验证的收尾与继续检查的行为比较，使训练关注完成判断。偏好标签必须来自真实任务要求，不能简单奖励更长的回答。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行离线演示，检查每对样本的上下文、偏好与非偏好响应。确认两者的关键区别后，再按技术参考准备模型训练，并在未见任务和正常完成任务上一起评估。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py
```

## 怎样解释结果

离线演示中的模拟分数不代表训练收益。真实评估还应检查过度检查、无法结束以及原有任务能力退化，避免把“永不宣布完成”训练成替代行为。

## 继续思考

怎样构造已经充分验证、应该及时结束的反例，防止模型学会无止境检查？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[build_preference_data.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/premature-completion-dpo/build_preference_data.py) → [train_dpo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/premature-completion-dpo/train_dpo.py) → [evaluate.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/premature-completion-dpo/evaluate.py) → [demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/premature-completion-dpo/demo.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

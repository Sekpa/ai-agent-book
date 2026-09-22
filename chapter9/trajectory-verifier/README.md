# 把运行轨迹变成有依据的学习信号

[本章实验目录](../README.md) · [相关正文](../../book/chapter9.md) · [技术参考](REFERENCE.md)

用户满意度或一个总分，很难告诉我们 Agent 应该改哪一步。本实验把客服轨迹拆成结果、过程与表达三个层次，学习如何给改进提供可定位的证据。

## 理解实验

结果层核对环境最终状态，过程层检查规则和承诺是否与动作一致，质量层评价较开放的表达与变通。不同层需要不同验证方式，不能全部交给一个模糊评分。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行本地演示，对照正常退款、虚假承诺和过度拒绝等样例。找到每个问题对应的轨迹轮次，再阅读验证器怎样得出判断。理解后才把启发式质量评分替换为真实模型裁判。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py
```

## 怎样解释结果

默认演示的质量层采用确定性方法，只用于解释结构。检查时既要看问题被识别出来，也要看正常行为是否被误判，并用专家标签校准。

## 继续思考

Agent 说“退款已完成”，但实际只查询了订单，这个问题应该在哪一层被发现？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/trajectory-verifier/demo.py) → [verifier.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/trajectory-verifier/verifier.py) → [consistency_checker.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/trajectory-verifier/consistency_checker.py) → [calibration.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/trajectory-verifier/calibration.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

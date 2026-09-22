# 用成对音频比较语音微调效果

[本章实验目录](../README.md) · [相关正文](../../book/chapter8.md) · [技术参考](REFERENCE.md)

一次语音微调改变了什么，最直观的证据是同一文本训练前后的实际声音。本项目将音色一致性与声学事件控制分成两条比较路径。

## 理解实验

固定输入文本和生成条件，可以更清楚地观察适配器的作用。留出损失、实际听感和目标事件检测分别提供不同证据；没有哪一个指标能独自概括全部语音质量。

## 动手之前

训练需要独立的数据与计算环境。先按技术参考核对数据准备、模型版本与硬件要求；第一次练习只检查少量样本和一个短流程。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先选择 Orpheus 或 Sesame 路线，阅读其数据与目标。按技术参考准备环境后，保留基础模型输出，再训练并生成对应音频。比较时交替听正向改善与负面案例，避免只挑最好的一段。

## 怎样解释结果

少量更新能演示学习过程，却不保证广泛泛化。兼容性失败也要与训练效果分开记录；模型根本没有正确加载时，后续音频不能用于比较。

## 继续思考

怎样组织盲听，让评价者不知道哪段来自微调后模型，又仍能判断目标特征？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[run_orpheus.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/speech-sft-experiment/run_orpheus.py) → [run_sesame.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/speech-sft-experiment/run_sesame.py) → [analyze_campaign.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/speech-sft-experiment/analyze_campaign.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

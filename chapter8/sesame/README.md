# 通过对齐数据学习语音表达

[本章实验目录](../README.md) · [相关正文](../../book/chapter8.md) · [技术参考](REFERENCE.md)

除了读出文字，语音模型还可能需要表达笑声、叹息等事件。本项目围绕 Sesame CSM 的微调与推理，学习控制标签和实际音频之间如何建立联系。

## 理解实验

标签只有与声音稳定对应时才有学习价值。模型接收的序列格式、说话人信息与音频编码必须一致；推理时遗漏其中一项，就可能与训练分布不匹配。

## 动手之前

训练需要独立的数据与计算环境。先按技术参考核对数据准备、模型版本与硬件要求；第一次练习只检查少量样本和一个短流程。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先按技术参考建立独立环境，检查一个训练样本中的文本、控制标签与音频。完成短训练后，用未见句子分别带标签和不带标签生成声音，再比较事件是否在合适位置出现。

## 怎样解释结果

不要只看输出 WAV 是否可播放。应检查文字内容、事件类型、出现时机和说话人一致性；标签被模型忽略与音频解码失败是不同问题。

## 继续思考

如果训练集中每个叹息都位于句首，模型能否学会在句中表达？怎样补充数据？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[sesame_csm_sft_unsloth.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/sesame/sesame_csm_sft_unsloth.py) → [inference.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/sesame/inference.py) → [batch_inference.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/sesame/batch_inference.py) → [example_inputs.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/sesame/example_inputs.json)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

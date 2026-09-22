# 比较学习文本分布与学习指令回答

[本章实验目录](../README.md) · [相关正文](../../book/chapter8.md) · [技术参考](REFERENCE.md)

让模型适应一种语言，既涉及理解该语言的文本，也涉及按指令完成任务。本实验先继续预训练，再进行监督微调，观察两个阶段带来的不同变化。

## 理解实验

继续预训练使用普通语料的预测目标，指令微调使用输入与目标回答。二者不能简单互换：流畅续写不等于会回答指令，遵循示范也不代表掌握了所有领域知识。

## 动手之前

训练需要独立的数据与计算环境。先按技术参考核对数据准备、模型版本与硬件要求；第一次练习只检查少量样本和一个短流程。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先查看韩语文本样本和指令样本，比较字段与标签构造。按技术参考准备基础模型和独立训练环境，从小数据比例开始。用同一组留出问题比较原模型、继续预训练后模型与微调后模型。

## 怎样解释结果

分别检查语言流畅度、指令完成情况和原有能力是否退化。不要预先假设基础模型完全不懂目标语言，应先测量基线。

## 继续思考

如果继续预训练提高了文本预测能力，却降低了指令遵循，后续数据应怎样设计？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[continued-pretrain.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/continued-pretraining/continued-pretrain.py) → [evaluate_model.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/continued-pretraining/evaluate_model.py) → [compare_models.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/continued-pretraining/compare_models.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

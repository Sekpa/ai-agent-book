# 把长提示词中的行为转成训练样例

[本章实验目录](../README.md) · [相关正文](../../book/chapter8.md) · [技术参考](REFERENCE.md)

一个长提示词可能稳定引导模型完成任务，但每次请求都携带它会增加成本。本实验让教师在完整提示下产生样例，再训练学生在更短输入下完成相似任务。

## 理解实验

蒸馏转移的是样例中体现的行为，不会自动复制提示词的全部含义。训练分布未覆盖的边界条件，学生可能学不到。减少输入与推理开销的收益也需要与准确率共同测量。

## 动手之前

训练需要独立的数据与计算环境。先按技术参考核对数据准备、模型版本与硬件要求；第一次练习只检查少量样本和一个短流程。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先读教师提示和生成样本，选择一条规则追踪它如何体现在目标输出中。按技术参考准备独立训练环境，训练后在未见输入上比较教师、原始学生与微调学生。

## 怎样解释结果

不能预先承诺学生具有相同能力。应分别检查任务质量、输出格式、延迟和输入量，并专门测试提示中重要但少见的条件。

## 继续思考

一条规则在训练样例里从未真正触发，学生有没有机会学会它？怎样补充覆盖？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[create_data.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/prompt-distillation/create_data.py) → [train_sft_trl.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/prompt-distillation/train_sft_trl.py) → [evaluate.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/prompt-distillation/evaluate.py) → [compare.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/prompt-distillation/compare.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 从教师轨迹构造学生训练数据

[本章实验目录](../README.md) · [相关正文](../../book/chapter8.md) · [技术参考](REFERENCE.md)

教师模型的回答可能包含有用步骤，也可能包含错误或冗余。本实验从生成、验证、筛选到训练学生，学习为什么蒸馏质量取决于数据处理，而不只是教师更强。

## 理解实验

教师轨迹先经过答案检查，再转成监督样本。训练时需要区分输入与目标词元，避免把不该预测的部分计入损失。学生评估使用未见题目，才能检查学到的是否超过样例记忆。

## 动手之前

运行模型部分需要按技术参考配置对应的服务凭据；调用会使用该服务的额度。先准备一个小任务，再扩展比较范围。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先只生成少量轨迹，人工核对题目、推理与答案。查看数据审计结果，确认错误样本怎样被处理，再按技术参考运行学生训练与成对评估。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python generate_data.py --max_problems 2
```

## 怎样解释结果

最终答案正确不一定保证每个中间步骤都正确。还要观察教师轨迹是否包含反思或回溯，以及学生在新题上是否保持这种有用行为。

## 继续思考

一条很长但正确的轨迹与一条简短正确的轨迹，哪条更适合学生？需要依据什么比较？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[generate_data.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/cot-distillation/generate_data.py) → [sft_data_auditor.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/cot-distillation/sft_data_auditor.py) → [train_student.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/cot-distillation/train_student.py) → [evaluate_student.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/cot-distillation/evaluate_student.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

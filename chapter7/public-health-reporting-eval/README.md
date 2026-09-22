# 用合成报表数据练习可验证评价

[本章实验目录](../README.md) · [相关正文](../../book/chapter7.md) · [技术参考](REFERENCE.md)

报表 Agent 不仅要给出数字，还要说明数字来自哪些记录。本项目使用合成的汇总数据，练习工具使用、答案依据和结构化评分，不涉及真实诊疗。

## 理解实验

样例工具提供可计算的数据，预期答案提供独立参照，评分器检查数值与陈述。这样可以发现“部分数字正确，但附加解释没有依据”的情况。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读一个任务、工具数据和预期答案，手工核对计算。再按技术参考准备预测文件，运行评分器；刻意比较完整回答与遗漏来源的回答，观察各项分数如何变化。

## 怎样解释结果

这是合成数据上的教学案例，不能代表某个真实公共卫生系统的部署质量。检查报告时还应区分数据缺失与模型凭空补充，避免把二者合成一个错误类别。

## 继续思考

当所需统计期的数据缺失时，一个合格回答应该怎样表达已知范围与缺口？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[tasks.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/public-health-reporting-eval/tasks.json) → [reporting_tools.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/public-health-reporting-eval/reporting_tools.py) → [evaluator.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/public-health-reporting-eval/evaluator.py) → [expected_answers.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/public-health-reporting-eval/expected_answers.json)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

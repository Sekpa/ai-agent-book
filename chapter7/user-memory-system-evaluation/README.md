# 对照记忆系统的完整处理链

[本章实验目录](../README.md) · [相关正文](../../book/chapter7.md) · [技术参考](REFERENCE.md)

评价记忆系统时，只比较几段预先写好的回答无法反映实际存储与检索。本实验在相同对话材料上运行不同记忆配置，检查从构建记忆到生成回答的全过程。

## 理解实验

JSON 卡片、RAG 和混合路径使用不同表示与检索方式。每个用例应独立建立状态，避免上一题的信息泄漏到下一题。模型裁判还需要校准，才能知道分数与人工判断是否一致。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先选一条案例，阅读对话、问题与评分依据。配置后运行单题路径，检查实际建立的记忆和回答时取出的内容。理解后再比较多种配置，最后汇总不同层次案例的成绩。

## 怎样解释结果

一套系统得分低，可能是提取丢失、检索失败或回答误用。沿完整轨迹定位，比直接更换回答模型更有依据。裁判不一致的案例应回到评分规则核对。

## 继续思考

两个系统答案相同，但一个读取了大量无关历史，评价中还应包含哪些成本指标？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[experiment.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/user-memory-system-evaluation/experiment.py) → [default_config.yaml](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/user-memory-system-evaluation/default_config.yaml) → [calibration_summary.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/user-memory-system-evaluation/calibration_summary.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 把逻辑谜题写成约束问题

[本章实验目录](../README.md) · [相关正文](../../book/chapter5.md) · [技术参考](REFERENCE.md)

骑士总说真话，无赖总说假话。人物增加后，只靠文字推演容易遗漏条件。本实验把这类谜题写成变量与约束，学习如何用求解器系统地检查可能答案。

## 理解实验

变量表示每个人的身份，约束表示身份与陈述之间必须满足的关系。求解器枚举或剪枝寻找满足全部约束的赋值。它保证的是形式化模型的解，前提是自然语言条件被正确翻译。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行离线求解器，选一题手工列出变量和约束，再与代码比较。理解形式化表示后，再配置模型比较纯推理和代码辅助路径，尤其检查模型有没有漏写某人的陈述。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py --mode solver
```

## 怎样解释结果

无解可能说明题目矛盾，也可能是翻译错误；多解则说明条件不足。不能因为得到一个答案就忽略其他满足条件的赋值。

## 继续思考

怎样用反例检查模型写出的约束，确实对应题目里的“当且仅当”？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/code-for-logic/demo.py) → [csp_solver.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/code-for-logic/csp_solver.py) → [puzzles.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/code-for-logic/puzzles.json)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

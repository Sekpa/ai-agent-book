# 遇到新日志格式时生成解析器

[本章实验目录](../README.md) · [相关正文](../../book/chapter5.md) · [技术参考](REFERENCE.md)

服务升级后，日志格式改变，原来的解析规则可能失效。本实验把新格式识别、解析代码生成和测试连接起来，学习怎样让系统在验证后接纳新的处理能力。

## 理解实验

未知格式先进入候选解析流程，生成的函数必须符合既定输入输出约定。测试通过后，执行引擎才使用它。生成、验证和加载分开，能避免把未经检查的代码直接用于后续数据。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读一条已知格式和一条新格式的样例，写出期望的结构化字段。按技术参考运行演示，跟踪新解析器怎样产生、测试和进入引擎。随后改变样例中的字段顺序，检查它是否只是记住了第一条日志。

## 怎样解释结果

一条样例解析成功不代表支持整个格式。应补充缺字段、异常值和格式近似的反例，并检查新解析器是否破坏旧格式处理。

## 继续思考

解析器失败时，应把整行丢弃、保留原文，还是转交人工？选择依据是什么？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/adaptive-log-parser/demo.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/adaptive-log-parser/agent.py) → [tester.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/adaptive-log-parser/tester.py) → [engine.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/adaptive-log-parser/engine.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

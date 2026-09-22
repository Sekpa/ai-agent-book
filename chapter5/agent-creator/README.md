# 生成一个专用 Agent 需要交付什么

[本章实验目录](../README.md) · [相关正文](../../book/chapter5.md) · [技术参考](REFERENCE.md)

让 Agent“再创建一个 Agent”，不是只写一段系统提示词。本实验从需求出发生成专用程序，并与复用已有框架的路径比较，学习如何判断生成结果是否真的可用。

## 理解实验

专用 Agent 需要明确任务、可用工具、控制流程和完成条件。复用框架可以减少基础设施工作，从零实现则更自由；两者都必须经过行为检查，不能只比较生成文件的数量。

## 动手之前

运行模型部分需要按技术参考配置对应的服务凭据；调用会使用该服务的额度。先准备一个小任务，再扩展比较范围。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读默认需求与验证器，写出专用 Agent 应完成的一个正常任务和一个边界情形。配置模型后运行生成流程，再检查产物结构、依赖与验证结果。最后改变需求中的一项，观察哪些部分需要重新生成。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py --output runs/release-agent
```

## 怎样解释结果

生成脚本成功结束不等于产物可以独立运行。还应确认工具调用、错误处理和输出证据与需求一致。验证器覆盖不到的行为需要单独说明。

## 继续思考

哪些职责应该由生成的 Agent 自己完成，哪些基础能力适合从已有框架继承？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/agent-creator/demo.py) → [creator.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/agent-creator/creator.py) → [validator.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/agent-creator/validator.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 理解一个编码 Agent 的完整工作循环

[本章实验目录](../README.md) · [相关正文](../../book/chapter5.md) · [技术参考](REFERENCE.md)

编码 Agent 不只是一次生成代码：它需要查看文件、理解任务、修改内容、运行检查并处理错误。本项目把这些步骤放在一个可阅读的 Python 实现中，便于你逐层跟踪。

## 理解实验

模型决定下一步动作，工具负责文件与程序操作，状态管理记录当前进展。每轮执行结果再次进入上下文，模型才有机会根据真实反馈修正代码。工具目录与可用权限共同限定它能够做什么。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先列出工具，再阅读工具注册表，理解每个工具接收什么参数。按技术参考配置模型后，在独立练习目录中完成一个小程序任务：生成问候函数、运行它，再修改一个需求。观察每次改动对应的检查。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py --list-tools
```

## 怎样解释结果

生成文件、程序运行和需求满足应分别验证。若检查失败，沿轨迹判断模型是在修正根因，还是不断修改与错误无关的内容。这里是理解工程机制的教学实现，不能仅凭工具齐全就认定适合所有生产环境。

## 继续思考

当模型连续多次修改仍未通过检查，控制循环应该何时停止并向用户说明问题？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[main.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/coding-agent/main.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/coding-agent/agent.py) → [tool_registry.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/coding-agent/tool_registry.py) → [system_state.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/coding-agent/system_state.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

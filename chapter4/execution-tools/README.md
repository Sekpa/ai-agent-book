# 从提出动作到确认动作已经完成

[本章实验目录](../README.md) · [相关正文](../../book/chapter4.md) · [技术参考](REFERENCE.md)

Agent 生成一条命令，并不代表命令已经成功执行。本实验围绕执行工具学习完整动作链：接收参数、检查条件、执行操作，再把结果交回模型。

## 理解实验

执行层需要描述成功与失败，也要处理过长输出、保存结果和后续验证。模型生成的“完成了”只是一段文字；可靠判断应来自退出状态、文件变化或任务专用检查。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先在可丢弃的工作目录中运行离线示例，观察一次文件或代码操作。阅读工具返回的状态与输出，再打开生成文件核对。熟悉这条路径后，才把同样的结果处理方式用于更复杂的任务。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python cli.py demo
```

## 怎样解释结果

区分命令结束、执行成功和任务目标达成。输出被截断时，要知道完整结果保存在何处；错误消息也应保留足够信息，帮助决定修正参数还是停止操作。

## 继续思考

程序返回零退出码，但生成文件内容错误，应该由哪一层发现问题？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[cli.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/execution-tools/cli.py) → [execution_tools.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/execution-tools/execution_tools.py) → [file_tools.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/execution-tools/file_tools.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

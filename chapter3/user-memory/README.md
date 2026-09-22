# 把对话历史转成可持续更新的用户记忆

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

保存全部聊天记录，不等于下次对话能用上相关信息。本实验把交互与后台记忆处理分开，学习怎样从对话提取候选事实、更新存储，并在后续回答中检索它们。

## 理解实验

对话模块负责当前响应，后台模块负责整理长期信息。这样可以区分“刚才说过什么”与“值得长期保留什么”。不同存储模式改变组织方式，却都需要处理来源、冲突和时间变化。

## 动手之前

运行模型部分需要按技术参考配置对应的服务凭据；调用会使用该服务的额度。先准备一个小任务，再扩展比较范围。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

配置模型后先运行演示。对照一轮原始对话、后台提取的内容和后续回答，再修改一个用户事实继续观察。读代码时先看对话模块怎样读取记忆，再看后台处理器什么时候提交更新。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py --mode demo --memory-mode enhanced_notes
```

## 怎样解释结果

检查系统是否把临时计划误写成永久偏好，或把模型自己的猜测保存成用户事实。回答提到了某条信息，也应能追溯到用户真正说过的内容。

## 继续思考

哪些信息只应该保留在本轮上下文，哪些适合长期存储？用户纠正事实时应发生哪些更新？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[conversational_agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/user-memory/conversational_agent.py) → [background_memory_processor.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/user-memory/background_memory_processor.py) → [memory_manager.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/user-memory/memory_manager.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

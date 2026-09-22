# 让本地模型通过工具完成任务

[本章实验目录](../README.md) · [相关正文](../../book/chapter2.md) · [技术参考](REFERENCE.md)

本地部署解决的是“在哪里运行模型”，工具调用解决的是“模型怎样请求外部能力”。本实验把两者连接起来，帮助你理解一个兼容接口背后的模型服务、工具协议和执行循环。

## 理解实验

模型服务接收消息并生成文本或工具调用；客户端负责识别调用、执行工具和返回结果。支持同一种 HTTP 接口，并不意味着所有模型都能稳定产生相同的工具结构，服务端的模板与解析方式也会影响行为。

## 动手之前

本节需要本地模型或服务。先按技术参考确认模型文件、运行后端与内存或显存要求，再进行下面的练习。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

按技术参考安装并启动 Ollama，准备示例模型，再运行客户端。先完成一次普通对话，然后提出需要天气工具的请求。逐步检查服务是否收到请求、模型是否输出工具调用，以及客户端是否把执行结果送回模型。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py --backend ollama
```

## 怎样解释结果

把模型回答、工具返回值和最终解释分开阅读。示例工具中的固定数据只能说明流程，不能作为实时天气信息。若调用失败，先定位模型服务、调用解析还是工具执行层，再决定修改哪一部分。

## 继续思考

一个模型能正确生成 JSON，是否足以证明它能完成多轮工具调用？还缺少哪些行为？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[main.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/local_llm_serving/main.py) → [server.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/local_llm_serving/server.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/local_llm_serving/agent.py) → [tools.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/local_llm_serving/tools.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

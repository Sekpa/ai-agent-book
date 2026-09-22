# 把搜索得到的信息交给代码计算

[本章实验目录](../README.md) · [相关正文](../../book/chapter1.md) · [技术参考](REFERENCE.md)

“两个城市相距多远”同时包含事实查询和数值计算。只让模型凭记忆作答，难以核对数据来源；只运行程序，又缺少输入数据。本实验把搜索与代码执行串起来，观察 Agent 怎样完成这类复合任务。

## 理解实验

模型先决定需要哪些信息，再调用托管搜索和代码执行工具。搜索结果提供可追溯的数据，代码把数据转成可检查的计算。回答中的引用与计算过程应能对应起来，才能判断结论是怎样得到的。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先读 `example_request.py` 和技术参考中的请求示例，识别模型、工具、用户需求三个部分。再选一个支持相应托管工具的后端，完成凭据配置，运行单次查询。不要把“请求里写了工具名”当作工具确实执行过。

## 怎样解释结果

在轨迹中寻找搜索、代码执行和最终答案三个环节。若使用城市距离问题，还应检查坐标来源、距离公式和参与比较的城市集合。一个格式漂亮的表格不足以证明计算正确；缺少的国家或错误坐标都会改变最近的一对。

## 继续思考

用户只说“做一份城市距离分析”时，哪些条件应该先澄清，哪些可以在回答中说明假设？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[example_request.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/search-codegen/example_request.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/search-codegen/agent.py) → [main.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/search-codegen/main.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

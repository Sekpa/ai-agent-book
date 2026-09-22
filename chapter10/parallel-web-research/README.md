# 并行收集资料时怎样保持证据一致

[本章实验目录](../README.md) · [相关正文](../../book/chapter10.md) · [技术参考](REFERENCE.md)

查阅多个来源可以并行进行，但最后仍需要判断它们是否描述同一个对象。本实验让多个浏览器工作者各自读取来源，再把有出处的结果交给管理者整理。

## 理解实验

独立浏览器上下文减少工作者互相影响，任务标识与消息总线帮助管理者追踪进度。并行减少等待，但不会自动解决同名对象、冲突资料或来源质量问题。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读站点配置和目标名称，明确每个工作者负责的来源。按技术参考准备浏览器与模型后，从少量来源开始，跟踪启动、返回、追问与终止消息，再检查汇总是否保留出处。

## 怎样解释结果

某个工作者失败时，汇总应说明缺口，而不是让其他结果假装覆盖全部来源。还要比较协调开销与实际节省的时间。

## 继续思考

两个来源对同一人的职位给出不同信息，管理者应怎样利用日期和来源解释差异？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[agents.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/parallel-web-research/agents.py) → [message_bus.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/parallel-web-research/message_bus.py) → [sources.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/parallel-web-research/sources.py) → [demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/parallel-web-research/demo.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 让 Agent 响应定时器和外部事件

[本章实验目录](../README.md) · [相关正文](../../book/chapter6.md) · [技术参考](REFERENCE.md)

Agent 不一定每次都由用户发一句话启动。定时任务、文件变化和外部消息也可以触发工作。本实验先用本地事件理解事件到任务的转换。

## 理解实验

事件循环接收事件、排队并交给处理逻辑。触发发生与任务完成是两个时刻；周期事件还可能在上一次处理结束前再次到达。把事件类型和处理状态分开，才容易解释等待与重复执行。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行一次短定时器演示，观察计时结束、事件进入队列和处理结果三个环节。再按技术参考尝试周期事件或文件观察。理解本地路径后，才接入真实模型和外部来源。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python event_loop_demo.py --mock --trigger timer --delay 2 --duration 6
```

## 怎样解释结果

模拟处理器不产生真实模型决策，但能展示事件调度。检查重复事件是否导致重复任务、退出时还有没有待处理事件，以及异常是否被清楚记录。

## 继续思考

如果一个周期任务的执行时间超过触发间隔，应排队、合并，还是跳过本轮？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[event_loop_demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/agent-with-event-trigger/event_loop_demo.py) → [event_types.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/agent-with-event-trigger/event_types.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/agent-with-event-trigger/agent.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 区分用户画像与事件记忆

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

“用户偏好简短回答”和“用户昨天改了会议时间”都是记忆，却有不同的时间特征。本实验围绕画像与事件两类信息，解释记忆系统为什么需要多种表示。

## 理解实验

画像总结相对稳定的属性，事件保留发生时间和具体经过。本目录既包含连接真实 Memobase 服务的演示，也包含手写的教学实现。它们可以帮助理解相似概念，但不能把手写实现的结果当作框架本身的性能。

## 动手之前

运行模型部分需要按技术参考配置对应的服务凭据；调用会使用该服务的额度。先准备一个小任务，再扩展比较范围。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先用手写演示追踪一条信息的保存与查询。随后按技术参考启动 Memobase 服务，阅读并运行 `profile_demo.py`，比较框架返回的画像与事件。每次比较都应记录实际采用了哪条实现路径。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py --mode demo
```

## 怎样解释结果

观察临时事件有没有被错误概括为稳定属性，时间更新是否保留，以及回答是否使用了恰当的记忆类别。不要仅凭字段名称一致就认定两套实现行为相同。

## 继续思考

用户连续三次选择同一种酒店，何时可以把事件概括成偏好？这种概括还应保留什么证据？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[main.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/memobase/main.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/memobase/agent.py) → [profile_demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/memobase/profile_demo.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

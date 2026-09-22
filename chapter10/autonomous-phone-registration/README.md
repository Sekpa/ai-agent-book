# 让浏览器与语音角色协作补齐表单信息

[本章实验目录](../README.md) · [相关正文](../../book/chapter10.md) · [技术参考](REFERENCE.md)

浏览器 Agent 遇到缺失字段时，可以向用户询问，而不是猜测。本实验将页面观察与语音交互结合，学习协作者怎样共享任务状态并等待必要信息。

## 理解实验

浏览器角色发现字段要求，语音角色收集用户回答，协调层把信息交回正在等待的任务。字段语义、来源和确认状态需要保持对应，才能避免把一次回答用于错误位置。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读本地测试表单和消息模型，找出哪些字段由页面提供、哪些必须由用户说明。按技术参考使用本地演示路径，并在明确同意参与后进入语音会话，观察补充信息怎样返回表单。

## 怎样解释结果

核对填写值是否来自本次用户回答，是否在缺信息时等待，以及提交前是否满足任务条件。本地测试表单与真实网站操作应分开，演示过程无需注册外部账号。

## 继续思考

用户修改前面已经填写的答案时，两个角色怎样避免继续使用过期值？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[models.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/autonomous-phone-registration/models.py) → [bus.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/autonomous-phone-registration/bus.py) → [orchestration.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/autonomous-phone-registration/orchestration.py) → [decision.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/autonomous-phone-registration/decision.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 通过截图与动作理解 Computer Use

[本章实验目录](../README.md) · [相关正文](../../book/chapter6.md) · [技术参考](REFERENCE.md)

电脑操作 Agent 通过屏幕观察状态，再提出点击、输入等动作。本项目用提供商原生协议展示这一闭环，帮助你理解视觉输入与桌面操作之间的连接。

## 理解实验

截图是观察，结构化动作是请求，桌面环境负责实际执行。动作后需要新的截图，才能判断页面是否发生了预期变化。坐标正确并不意味着任务完成，界面还可能加载中或出现额外提示。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读已有天气查询轨迹，将每张截图与下一次动作配对。需要重新运行时，按技术参考准备官方容器与服务凭据，使用同样的只读查询任务。先确认环境输入输出，再观察模型决策。

## 怎样解释结果

检查最终天气信息是否来自目标页面，以及动作是否始终围绕查询目的。已有记录限定在这个任务与环境中，不表示已经验证通用桌面操作能力。

## 继续思考

界面布局变化后，哪种状态检查能避免模型继续使用上一张截图中的坐标？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[run_weather_task.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/claude-computer-use-native/run_weather_task.py) → [validate_weather_run.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/claude-computer-use-native/validate_weather_run.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。
